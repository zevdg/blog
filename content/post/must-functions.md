---
title: Must functions
date: 2018-01-01
publishDate: 9999-01-01 # hide this post for now
---

# Must functions

Last week, I was perusing the

https://github.com/golang/go/issues/22122

There are 2 patterns in the standard library and builtin types that are worth mentioning in this discussion: the options second `ok` return for map access and channel reads and `Must*` Functions. Both of these mechanisms are ways for the caller of a function specify if the function (or operation) they are calling should panic or return an error to be heandled by the caller. I'm mostly gonna focus on the `Must*` functions as they are the more enlightening example IMO, but some of this stuff applies to the map accessor and channel read operators as well.

Example: [regexp.MustCompile](https://golang.org/pkg/regexp/#MustCompile)

Consider these 3 code snippets which are [roughly](https://golang.org/src/regexp/regexp.go?s=8678:8714#L227) equivalent

```go
// Snippet A
reStr := "(gopher){2}"
re, err := regexp.Compile(reStr)
if err != nil {
    panic(`regexp: Compile(` + strconv.Quote(reStr) + `): ` + error.Error())
}
fmt.Println(re.MatchString("gopher"))
```

```go
// Snippet B
re := regexp.MustCompile("(gopher){2}")
fmt.Println(re.MatchString("gopher"))
```

```go
// Snippet C
fmt.Println(regexp.MustCompile("(gopher){2}")re.MatchString("gopher"))
```

The existance of the `MustCompile` function tells us 2 things about the authors of this pacakge (at least at the time the wrote these functions).

1.  In many situations, it is reasonable, appropriate, and decidedly not an anti-pattern to panic if `regexp.Compile` fails.  
    _probably, they were thinking of the relatively common case where the string passed to `regexp.Compile` is a constant_
2.  Snippet B and/or Snippet C are not only preferable to Snippet A, but so much "better" that it justified adding both `regexp.MustCompile` and `regexp.MustCompilePOSIX` to the public API.

To be clear, both of these points are matters of opinion and very debatable. All I'm saying is that someone wrote this code and someone else approved it. Unless I'm missing something, both of those people must have thought these 2 things.

The gist of this proposal is that all functions should have a `Must*` form. However, if we compare the proposal to `regexp.MustCompile`, we notice a few small differences.

With this new syntax, we could imagine that Go 2 might remove `regexp.MustCompile` in favor of the following snippet.

```go
re, # := regexp.Compile("(gopher){2}")
fmt.Println(re.MatchString("gopher"))
```

This looks like Snippet B, but as per this proposal, it isn't exactly the same.
This is actually equivalent to

```go
re, err := regexp.Compile("(gopher){2}")
if err != nil {
    panic(err)
}
fmt.Println(re.MatchString("gopher"))
```

which prints significantly less useful information than Snippet A. However, this is a detail of the proposal that could easily be fixed. IMO the behavior of this hypothetical # operator would be significantly more useful if it were shorhand for something along the lines of

```go
panic(fmt.Sprintf("%s: %s(%s):%s", packageName, functionName, argsList, err))
```

making it roughly equivalent to the behavior of `regexp.MustCompile`.

The more complicated difference between `Must*` functions and this proposal concerns Snippet C. Sometimes, the point of these `Must*` functions (and of some similar proposals) is to allow the [chaining together of commands](https://www.calhoun.io/using-functional-options-instead-of-method-chaining-in-go/) like we do in Snippet C. The syntax you've proposed doesn't seem to allow function chaining. This could theoretically be "fixed" but it opens up a whole other can of worms, so I'm gonna assume that it was intentional and move on.

Ok, if you're still with me, there's one last difference between this proposal and `Must*` functions and it is both the best argument for **and** the best argument against this proposal.

`Must*` functions are created by the library author. The power is up to them to decide which functions are appriate to have a "panicy" option alongside the normal `(result, error)` varient. To be fair, the caller can always `panic` manually or write a helper function like [template.Must](https://golang.org/pkg/html/template/#Must) for specific return types, but they cannot make a generic one like [this proposal](https://github.com/golang/go/issues/21419) advocates. However, in general, in cases where a `panic` is sensible, it's up to the library author to provide that alternate API. The question is, is that a good or a bad thing?

Interestingly enough, the `go` keyword we know and love is almost a prefect analogy to this proposed feature. The `go` keyword is awesome because it lets the **caller** decide if a function should be run synchronously or asynchronously. Other languages often require library writers to anticipate when a function may need to be called [synchronously](https://nodejs.org/api/fs.html#fs_fs_opensync_path_flags_mode) vs [asynchronously](https://nodejs.org/api/fs.html#fs_fs_open_path_flags_mode_callback) and proved 2 different versions of the function in their public API. Look familiar? The Go authors decided that even though many functions/libraries are never called asynchronously, it's better to let the lib authors create a single synchronous function and give the callers a way to call it asynchonously if/when they need to. This proposal is sorta like the `go` keyword but for the caller to invoke a non-panicing function in a panicy way instead of invoking a synchronous function asychronously.

So that all sounds well and good, but there's a subtle difference. Giving peolpe an easy way to make a synchonous function asyncronous is generally not abused. Sure, people can and do make overly complex asynchorous programs when a simpler synchonous program would have sufficed, but it's relatively rare. Giving people who are used to exceptions and easy way to panic any function is almost surely going to be abused more than the `go` keyword. Now if we did a really good job educating people, we _might_ be able to prevent it from getting out of hand, but is this little bit of syntactic sugar really worth the risk? I honestly don't have a strong opinion, but I hope this brain dump helped someone.
