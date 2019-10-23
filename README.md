# Elm Tailwind

[tailwind](https://tailwindcss.com) + [elm](http://elm-lang.org) = :rocket:

See the [demo](https://postcss-elm-tailwind-demo.onrender.com/) and [repo](https://github.com/monty5811/postcss-elm-tailwind/tree/master/demo).

[![Actions Status](https://github.com/monty5811/postcss-elm-tailwind/workflows/Node%20CI/badge.svg)](https://github.com/monty5811/postcss-elm-tailwind/actions)

```elm
view : Model -> Html Msg
view model =
    Html.div [ TW.h_screen, TW.w_screen, TW.flex, TW.justify_center, TW.items_center, TW.bg_gray_200 ]
        [ Html.div []
            [ Html.button
                [ E.onClick Decrement
                , TW.px_2
                , TW.px_4
                , TW.text_white
                , TW.bg_blue_500
                , TW.w_full
                ]
                [ Html.text "-" ]
            , Html.div
                [ TW.text_2xl
                , TW.text_center
                , TW.my_4
                ]
                [ Html.text (String.fromInt model) ]
            , Html.button
                [ E.onClick Increment
                , TW.px_2
                , TW.px_4
                , TW.text_white
                , TW.bg_blue_500
                , TW.w_full
                ]
                [ Html.text "+" ]
            ]
        ]
```

There are two ways to use this package:

## 1. Use the postcss plugin

The Elm code in this package is generated by a postcss [plugin](https://github.com/monty5811/postcss-elm-tailwind).

How to use:

* Install tailwind using the [postcss instructions](https://tailwindcss.com/docs/installation/#using-tailwind-with-postcss)
* Install the `postcss-elm-tailwind` plugin: `yarn add postcss-elm-tailwind`
* Add the plugin to your `postcss.config.js` - see the [demo for more info](https://github.com/monty5811/postcss-elm-tailwind/tree/master/demo)
----

* **Advantage**: Picks up any changes to your tailwind config & brings them into Elm
* **Disadvantage**: Little bit more time to setup, requires a build step for you CSS

## 2. With the default Tailwind build

> **Note** due to limitations with file upload size to packages.elm-lang.org, you
> will have to use [Skinney/elm-git-install](https://github.com/Skinney/elm-git-install)
> or some other method to install this package

* Add the default tailwind build to your site
* Install this package (`elm install monty5811/elm-tailwind`)
* Use in you elm code like so:

----

* **Advantage**: Minimal setup, easy to get started
* **Disadvantage**: Larger tailwind build & no customisation

## Caveats

1. If you have set a `prefix` in your tailwind config, you must tell
`postcss-elm-tailwind` what it is too in your `postcss.config.js`. [demo](https://github.com/monty5811/postcss-elm-tailwind/blob/master/demo/postcss.config.js#L15).
2. In order to get a small build, you'll need to build Tailwind twice - once
without purgecss to build `TW.elm` with all the classes and once with purgecss
so that all the unused classes are removed. [demo](https://github.com/monty5811/postcss-elm-tailwind/blob/master/demo/package.json#L18).
