# Description

Forked [syntax highlight plugin](https://www.11ty.dev/docs/plugins/syntaxhighlight/) with hardcoded line numbers into the markdown side of the plugin (in a not very nice or generic way). It's functional enough for my needs without losing other features, as past attempts to do it properly have failed (see below).

# Reason why this is done

I want to include code snippets with detailed explanations, so I need three things:
- Syntax highlighting for various code snippets.
- To highlight specific lines without using a sub-feature like `diff`.
- To have numbered lines for easy reference when describing the impact of specific lines.

And surprisingly, in the 11ty world, this is not as straightforward to achieve, despite other frameworks (like `Sphinx`) having this problem solved.

## Highlightjs
- Is the unofficial (from the Eleventy perspective) syntax highlighting library used by the Eleventy's libdoc theme.
- Highlightjs can be extended with a third-party plugin to support line numbers. It results them being displayed as tables, which requires additional styling adjustments and excludes some CSS rules to avoid affecting normal tables. As well as extra JS changes within libdoc's functions.
- Line number emphasis is not natively supported and is not easy to add such support.
- Does not align with the official documentation for Eleventy.

## Prismjs
- Libdoc based blog can be switched to 11ty-aligned Prismjs highlighter.
- The 11ty documentation will align with the actual behavior.
- Emphasis on lines works in vanilla, but line numbers do not work 11ty's syntax highlighting plugin
  - Despite the underlying prismjs framework having a plugin for them https://prismjs.com/plugins/line-numbers/
- Several **failed** attempts have been made to add support for line numbers:
  - One PR opened since 2019: https://github.com/11ty/eleventy-plugin-syntaxhighlight/pull/14
  - One closed (not-merged) PR: https://github.com/11ty/eleventy-plugin-syntaxhighlight/pull/24
  - There is a fork that support line numbers, but no longer supports line emphasis: https://www.npmjs.com/package/@pborenstein/eleventy-md-syntax-highlight

