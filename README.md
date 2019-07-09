# Webfont Generator CLI

> Easy-to-use, pre-configured cli tool to generate webfont icon kits from a bunch of .svg files

## Intro

> Forked from [@Workshape/icon-font-generator](https://github.com/Workshape/icon-font-generator)  

This cli utility is ment to make webfont icon sets creation from the command line really simple - It wraps and pre-configures [webfonts-generator](https://www.npmjs.com/package/webfonts-generator), but allows for some degree of customisation.

It also does a couple extra things such as creating a .json file containing the icons to unicode characters map, which may be later used in styles, templates, etc..

> It's recommended to run a [SVGO](https://github.com/svg/svgo) task before running this generator.

## Install
```
npm install AdrianoCahete/webfont-generator-cli#v2.2.0
```

## Use

### Quick usage

```
webfont-generator-cli my-icons/*.svg -o icon-dist
```

### Cli params

```
Usage   : webfont-generator-cli [ svg-icons-glob ] -o [ output-dir ] [ options ]

Example : webfont-generator-cli src/*.svg -o dist

Options:
  -o, --out        Output icon font set files to <out> directory
  -n, --name       Name to use for generated fonts and files (Default: icons)
  -s, --silent     Do not produce output logs other than errors (Default: false)
  -f, --fontspath  Relative path to fonts directory to use in output files (Default: ./)
  -c, --css        Generate CSS file if true (Default: true)
  --csspath        CSS output path (Defaults to <out>/<name>.css)
  --cssfontsurl    CSS fonts directory url (Defaults to relative path)
  --csstp          CSS handlebars template path (Optional)
  --html           Generate HTML preview file if true (Default: true)
  --htmlpath       HTML output path (Defaults to <out>/<name>.html)
  --types          Font types - (Defaults to 'svg, ttf, woff, woff2, eot')
  --htmltp         HTML handlebars template path (Optional)
  -j, --json       Generate JSON map file if true (Default: true)
  --jsonpath       JSON output path (Defaults to <out>/<name>.json)
  -p, --prefix     CSS classname prefix for icons (Default: icon)
  -t, --tag        CSS base tag for icons (Default: i)  
  --selector       Use a selector instead of 'tag + prefix' (Default: null)
  --normalize      Normalize icons sizes (Default: false)
  --round          Setup SVG rounding (Default: 10e12)
  --descent        Offset applied to the baseline (Default: 0)
  --mono           Make font monospace (Default: false)
  --height         Fixed font height value
  --center         Center font horizontally
  --timestamp      Override font creation time (Unix time stamp)
  --codepoint      The starting character code to count up from (Optional)
  --codepoints     Path to explicit character code mapping JSON file (Optional)
```

### Options

#### --codepoints
Codepoint needs to receive a `json` file with the follow template:
```
{
  "icon-name": "0xf100",
  "icon-name2": "0xf101",
}
```

Where the `[icon-name]` matchs an svg's file name.


## Know problems
  - If the font is super simplified, try pass `--height 1000` as parameter when generating the font.

  It occurs because the `round` parameter tends to simplify the SVG's path and may simplify too much.

## License

Copyright (c) 2019 Adriano Cahete - Released under the [MIT license](https://github.com/AdrianoCahete/webfont-generator-cli/blob/master/LICENSE)  
Original Copyright (c) 2014 Workshape.io Ltd. - Released under the [MIT license](https://github.com/Workshape/icon-font-generator/blob/master/LICENSE)
