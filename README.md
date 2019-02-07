## TinyMCE 4.9.4 - Personal version with several bugfixes and updates.


## DEMO:

https://lrusso.github.io/tinymce/demo.htm

## Changelog:

TYPE | ELEMENT | DETAILS
:---: | :---: | --- |
Added | Language Spanish | Complete translation.
Added | Theme Modern | Branding banner disabled.
Added | Plugin Save | Save menu item.
Added | Plugin Table | New tables with single border as default.
Added | Plugin ContextMenu | Table properties item in the context menu.
Added | Plugin Spellchecker | (No suggestions) item when there are no suggestions.
Added | TinyMCE Style | Light gray separator between the document and the status bar.
Added | In Demo Script | Implemented a script for uploading images into the document as base64.
Added | In Demo Script | Implemented a script that notifies when pasting external linked images.
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

## Spellchecker example image

![alt spellchecker](https://raw.githubusercontent.com/lrusso/tinymce/master/spellchecker.png)

## Spellchecker example code

```
tinymce.init(
    {
    selector: "textarea",
    plugins: "spellchecker",
    menubar: "tools",
    toolbar: "spellchecker",
    spellchecker_language: "en",
    spellchecker_languages: "English=en,Spanish=es",
    spellchecker_callback: function(method, text, success, failure)
        {
        tinymce.util.JSONRequest.sendRPC(
            {
            url: "/tinymce/spellchecker.php",
            method: "spellcheck",
            params:
                {
                lang: this.getLanguage(),
                words: text.match(this.getWordCharPattern())
                },
            success: function(result)
                {
                success(result);
                },
            error: function(error, xhr)
                {
                failure("Spellcheck error:" + xhr.status);
                }
            });
        }
    });
```

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
