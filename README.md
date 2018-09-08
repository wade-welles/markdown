markdown [![GoDoc](http://godoc.org/github.com/golang-commonmark/markdown?status.svg)](http://godoc.org/github.com/golang-commonmark/markdown) [![License](https://img.shields.io/badge/licence-BSD--2--Clause-blue.svg)](https://opensource.org/licenses/BSD-2-Clause) [![Build Status](https://travis-ci.org/golang-commonmark/markdown.png?branch=master)](https://travis-ci.org/golang-commonmark/markdown)]
========

golang-commonmark/markdown package provides CommonMark-compliant markdown parser and renderer, written in Go.

## Installation

    go get -u github.com/golang-commonmark/markdown

You can also go get [mdtool](https://github.com/golang-commonmark/mdtool), an example command-line tool:

    go get -u github.com/golang-commonmark/mdtool

## Standards support

Currently supported CommonMark spec: [v0.28](http://spec.commonmark.org/0.28/).

## Extensions

Besides the features required by CommonMark, golang-commonmark/markdown supports:

  * Tables (GFM)
  * Strikethrough (GFM)
  * Autoconverting plain-text URLs to links
  * Typographic replacements (smart quotes and other)

## Usage

``` go
md := markdown.New(markdown.XHTMLOutput(true))
fmt.Println(md.RenderToString([]byte("Header\n===\nText")))
```

Check out [the source of mdtool](https://github.com/golang-commonmark/mdtool/blob/master/main.go) for a more complete example.

The following options are currently supported:

  Name            |  Type     |                        Description                          | Default
  --------------- | --------- | ----------------------------------------------------------- | ---------
  HTML            | bool      | whether to enable raw HTML                                  | false
  Tables          | bool      | whether to enable GFM tables                                | true
  Linkify         | bool      | whether to autoconvert plain-text URLs to links             | true
  Typographer     | bool      | whether to enable typographic replacements                  | true
  Quotes          | string or | double + single quote replacement pairs for the typographer | “”‘’
                  | []string  |                                                             |
  MaxNesting      | int       | maximum nesting level                                       | 20
  LangPrefix      | string    | CSS language prefix for fenced blocks                       | language-
  Breaks          | bool      | whether to convert newlines inside paragraphs into `<br>`   | false
  Nofollow        | bool      | whether to add `rel="nofollow"` to links                    | false
  XHTMLOutput     | bool      | whether to output XHTML instead of HTML                     | false

## Benchmarks

Rendering spec/spec-0.28.txt on a Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz

    BenchmarkRenderSpecNoHTML         100    13671313 ns/op    4802790 B/op    23762 allocs/op
    BenchmarkRenderSpec               100    13914760 ns/op    4802199 B/op    23756 allocs/op
    BenchmarkRenderSpecBlackFriday    300     6058478 ns/op    2805064 B/op    17711 allocs/op

## See also

https://github.com/jgm/CommonMark — the reference CommonMark implementations in C and JavaScript,
  also contains the latest spec and an online demo.

http://talk.commonmark.org — the CommonMark forum, a good place to join together the efforts of the developers.
