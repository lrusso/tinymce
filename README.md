## TinyMCE 4.9.4 - Personal version with several bugfixes and updates.

## DEMOS:

DESCRIPTION | URL
:---: | --- |
Form saving example | https://lrusso.github.io/tinymce/demo1.htm
AJAX saving example | https://lrusso.github.io/tinymce/demo2.htm

## Changelog:

TYPE | ELEMENT | DETAILS
:---: | :---: | --- |
Update 1 | Language Spanish | Complete translation.
Update 2 | Theme Modern | Branding banner disabled.
Update 3 | Theme Modern | More font sizes available.
Update 4 | Theme Modern | Font sizes in "px" instead of "pt".
Update 5 | Theme Modern | Hides "px" in the font size list.
Update 6 | Plugin Save | Save menu item.
Update 7 | Plugin ContextMenu | Table properties item in the context menu.
Update 8 | Plugin Spellchecker | (No suggestions) item when there are no suggestions.
Update 9 | Plugin WordCount | Default cursor and non selectable on the wordcount value.
Update 10 | TinyMCE Style | Light gray separator between the document and the status bar.
Update 11 | TinyMCE Core | Added tinymce.activeEditor.getContent({format:"xml"}).
Update 12 | In Demo Script | Implemented a script that notifies when pasting external linked images.
Update 13 | In Demo Script | Implemented a script for uploading images into the document as base64.
Update 14 | In Demo Script | Implemented a script for adding spaces (tabs) when the Tab key is down.
Bugfix 1 | Plugin Spellchecker | Hides the suggestions when the spellchecker is disabled.
Bugfix 2 | Plugin Spellchecker | Prevents to move arround the document while spellchecking.
Bugfix 3 | Plugin Spellchecker | Prevents words remains marked when the user changes the language.
Bugfix 4 | Plugin Spellchecker | Prevents from making changes in a document thats starts with a table.
Bugfix 5 | Plugin Table | Prevents a table width to change when adding a column without width data.
Bugfix 6 | Plugin TextColor | Prevents from missplacing the X value in the transparent color cell.
Bugfix 7 | Plugin WordCount | Prevents from showing the wordcount as plural when one word written.
Bugfix 8 | Plugin CodeSample | Prevents from showing a vertical scrollbar in 720p devices.
Bugfix 9 | Skin LightGray | Fixes the max height possible for menus.
Bugfix 10 | Theme Modern | Prevents from changes in the viewport in mobile devices.
Bugfix 11 | Theme Modern | Using px instead of pt for better mobile devices performance.
Bugfix 12 | Theme Modern | Prevents from showing "Font Family" and "Font Size" when no content.
Bugfix 13 | TinyMCE Style | Prevents from showing extra large fonts in mobile devices.
Bugfix 14 | TinyMCE Core | Prevents from losing breaklines when copying and pasting a text.
Bugfix 15 | TinyMCE Core | File/New now clears the undo/redo history.
Bugfix 16 | TinyMCE Core | File/New now clears the dirty state.
Bugfix 17 | TinyMCE Core | Fixed that sometimes the align left and right didn't work.
Bugfix 18 | TinyMCE Core | Fixed that the alignment didn't work in strong tags.
Bugfix 19 | TinyMCE Core | Fixed tables with a wrong initial scroll top position in mobile devices.
Bugfix 20 | TinyMCE Core | Fixed that text styles didn't update on init when the document started with a table.

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
