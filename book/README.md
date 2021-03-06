<!--
# An Introduction to Elm
-->
# Elm について (はじめに)

<!--
**Elm is a functional language that compiles to JavaScript.** It competes with projects like React as a tool for creating websites and web apps. Elm has a very strong emphasis on simplicity, ease-of-use, and quality tooling.
-->

**Elm は JavaScript にコンパイルできる関数型プログラミング言語です。** ウェブサイトやウェブアプリケーションを作るツールという面では React のようなプロジェクトだと言えます。 Elm はシンプルであること、簡単に使えること、高品質であることを大切にしています。

<!--
This guide will:

  - Teach you the fundamentals of programming in Elm.
  - Show you how to make interactive apps with *The Elm Architecture*.
  - Emphasize principles and patterns that generalize to programming in any language.
-->
このガイドは以下のことを目指します。

  - Elm によるプログラミングの基礎を身に着けてもらうこと
  - *The Elm Architecture* を使ってインタラクティブなアプリケーションを作る方法をお見せすること
  - あらゆる言語で使える法則やパターンを重視すること

<!--
By the end I hope you will not only be able to create great web apps in Elm, but also understand the core ideas and patterns that make Elm nice to use.
-->
最終的にはあなたには Elm を使って素晴らしいウェブアプリをただ作れるようになるだけでなく、Elm をうまく使えるようになるための中心的なアイディアやパターンを理解してもらえればと思います。

<!--
If you are on the fence, I can safely guarantee that if you give Elm a shot and actually make a project in it, you will end up writing better JavaScript and React code. The ideas transfer pretty easily!
-->
Elm に対して様子見の立場である方も、Elm をちょっと試してみて実際に何かプロジェクトで使ってみると JavaScript や React のコードがいままでよりもうまく書けるようになっているはずです。 Elm で得られた知見はいろんなところで簡単に役立てることができます。

## A Quick Sample

Of course *I* think Elm is good, so look for yourself.

Here is [a simple counter](https://elm-lang.org/examples/buttons). If you look at the code, it just lets you increment and decrement the counter:

```elm
import Browser
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Browser.sandbox { init = 0, update = update, view = view }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

Notice that the `update` and `view` are entirely decoupled. You describe your HTML in a declarative way and Elm takes care of messing with the DOM.


## Why a *functional* language?

Forget what you have heard about functional programming. Fancy words, weird ideas, bad tooling. Barf. Elm is about:

  - No runtime errors in practice. No `null`. No `undefined` is not a function.
  - Friendly error messages that help you add features more quickly.
  - Well-architected code that *stays* well-architected as your app grows.
  - Automatically enforced semantic versioning for all Elm packages.

No combination of JS libraries can ever give you this, yet it is all free and easy in Elm. Now these nice things are *only* possible because Elm builds upon 40+ years of work on typed functional languages. So Elm is a functional language because the practical benefits are worth the couple hours you'll spend reading this guide.

I have put a huge emphasis on making Elm easy to learn and use, so all I ask is that you give Elm a shot and see what you think. I hope you will be pleasantly surprised!
