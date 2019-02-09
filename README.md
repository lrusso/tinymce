## TinyMCE 4.9.4 - Personal version with several bugfixes and updates.


## DEMO:

https://lrusso.github.io/tinymce/demo.htm

## Changelog:

TYPE | ELEMENT | DETAILS
:---: | :---: | --- |
Added | Language | Spanish complete translation.
Added | Theme Modern | Branding banner disabled.
Added | Plugin Save | Save menu item.
Added | Plugin Table | New tables with single border as default.
Added | Plugin ContextMenu | Table properties item in the context menu.
Added | Plugin Spellchecker | (No suggestions) item when there are no suggestions.
Added | Plugin WordCount | Default cursor and non selectable on the wordcount value.
Added | TinyMCE Style | Light gray separator between the document and the status bar.
Added | In Demo Script | Implemented a script that notifies when pasting external linked images.
Added | In Demo Script | Implemented a script for uploading images into the document as base64.
Bugfix 1 | Plugin Spellchecker | Hides the suggestions when the spellchecker is disabled.
Bugfix 2 | Plugin Spellchecker | Prevents to move arround the document while spellchecking.
Bugfix 3 | Plugin Spellchecker | Prevents words remains marked when the user changes the language.
Bugfix 4 | Plugin Table | Prevents a table width to change when adding a column without width data.
Bugfix 5 | Plugin TextColor | Prevents from missplacing the X value in the transparent color cell.
Bugfix 6 | Plugin WordCount | Prevents from showing the wordcount as plural when one word written.
Bugfix 7 | Plugin CodeSample | Prevents from showing a vertical scrollbar in 720p devices.
Bugfix 8 | Skin LightGray | Fixes the max height possible for menus.
Bugfix 9 | Theme Modern | Prevents from changes in the viewport in mobile devices.
Bugfix 10 | TinyMCE Style | Prevents from showing extra large fonts in mobile devices.
Bugfix 11 | TinyMCE Core | Prevents from losing breaklines when copying and pasting a text.
Bugfix 12 | TinyMCE Core | File/New now clears the undo/redo history.
Bugfix 13 | TinyMCE Core | File/New now clears the dirty state.
Bugfix 14 | TinyMCE Core | Fixed that sometimes the align left and right didn't work.
Bugfix 15 | TinyMCE Core | Fixed that the alignment didn't work in strong tags.

## Spellchecker example image

![alt spellchecker](https://raw.githubusercontent.com/lrusso/tinymce/master/spellchecker.png)

## Spellchecker example of a request to a server

```
{
"id":"c0",
"method":"spellcheck",
"params":
    {
    "lang":"en",
    "words":["this","is","a","test"]
    }
}
```

## Spellchecker example of a response from a server

```
{
"words":
    {
    "misspelled1": ["suggestion1", "suggestion2"],
    "misspelled2": ["suggestion1", "suggestion2"]
    }
}
```
## Example of setting for using BR instead of P

```
force_p_newlines: false,
force_br_newlines: true,
convert_newlines_to_brs: false,
remove_linebreaks: true,
forced_root_block : false
```

## Example of setting for extreme filter from external content

```
invalid_styles: "font-family font-size",
invalid_elements : "h1,h2,h3,h4,h5,h6,pre,code,p,div,input,textarea,sub,sup,hr,figure,article,iframe,header,footer,section,nav,aside,form,script",
valid_classes: "<*>SOME<*>IMPOSSIBLE<*>CLASSTYPE><*>",
paste_merge_formats: true,
```

## Example of setting for extreme clean formatting

```
formats:
    {
    removeformat:
        [
        {selector: "b,strong,em,i,font,u,strike", remove : "all", split : true, expand : false, block_expand: true, deep : true},
        {selector: "div", remove : "all"},
        {selector: "span", attributes : ["style", "class"], remove : "empty", split : true, expand : false, deep : true},
        {selector: "*", attributes : ["style", "class"], split : false, expand : false, deep : true}
        ]
    }
```
