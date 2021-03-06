## TinyMCE 4.9.4 - Personal version with several bugfixes and updates

## Demos

DESCRIPTION | URL
:---: | --- |
Form saving example | https://lrusso.github.io/tinyMCE/demo1.htm
AJAX saving example | https://lrusso.github.io/tinyMCE/demo2.htm

## Changelog

TYPE | ELEMENT | DETAILS
:---: | :---: | --- |
Fixed | Spellchecker | Prevents from removing the selected word.
Fixed | Spellchecker | Hides the suggestions when the spellchecker is disabled.
Fixed | Spellchecker | Prevents to move arround the document while spellchecking.
Fixed | Spellchecker | Prevents words remains marked when the user changes the language.
Fixed | Spellchecker | Prevents from making changes in a document thats starts with a table.
Fixed | Table | Prevents a table width to change when adding a column without width data.
Fixed | TextColor | Prevents from missplacing the X value in the transparent color cell.
Fixed | WordCount | Prevents from showing the wordcount as plural when one word written.
Fixed | CodeSample | Prevents from showing a vertical scrollbar in 720p devices.
Fixed | Template | Prevents from missplacing dialog window.
Fixed | Skin | Prevents from printing the corner handles when a image or table is selected.
Fixed | Skin | Fixes the max height possible for menus.
Fixed | Skin | Prevents from showing extra large fonts in mobile devices.
Fixed | Theme  | Prevents from changes in the viewport in mobile devices.
Fixed | Theme  | Using px instead of pt for better mobile devices performance.
Fixed | Theme  | Prevents from showing "Font Family" and "Font Size" when no content.
Fixed | Theme  | Prevents from showing templates with table cells with a 0px height when no content.
Fixed | Core | Prevents from losing breaklines when copying and pasting a text.
Fixed | Core | File/New now clears the undo/redo history.
Fixed | Core | File/New now clears the dirty state.
Fixed | Core | Fixed that sometimes the align left and right didn't work.
Fixed | Core | Fixed that the alignment didn't work in strong tags.
Fixed | Core | Fixed tables with a wrong initial scroll top position in mobile devices.
Updated | Spanish | Complete translation.
Updated | Theme | Branding banner disabled.
Updated | Theme | Font sizes in "px" instead of "pt".
Updated | Theme | Hides "px" in the font size list.
Updated | Save | Save menu item.
Updated | ContextMenu | Table properties item in the context menu.
Updated | Spellchecker | (No suggestions) item when there are no suggestions.
Updated | WordCount | Default cursor and non selectable on the wordcount value.
Updated | Skin | Light gray separator between the document and the status bar.
Updated | Core | Added tinymce.activeEditor.getContent({format:"xml"}).
Updated | Chart | Added my Chart plugin (https://github.com/lrusso/TinyMCEChartPlugin).
Updated | Spreadsheet | Added my Spreadsheet Plugin (https://github.com/lrusso/TinyMCESpreadsheetPlugin).
Updated | Demo Script | Implemented a script that notifies when pasting external linked images.
Updated | Demo Script | Implemented a script for uploading images into the document as base64.
Updated | Demo Script | Implemented a script for adding spaces (tabs) when the Tab key is down.

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

## Example of paste preprocess if extreme filter from external content used

```
paste_preprocess: function(plugin, args)
    {
    args.content = args.content.replace(new RegExp("</div>", "g"), "</div><br />");
    args.content = args.content.replace(new RegExp("</p>", "g"), "</p><br />");
    },
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
