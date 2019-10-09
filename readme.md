## iA Writer template with code highlighting

This is an output template for [iA Writer](https://ia.net/writer) with code highlighting implemented with [highlight.js](https://highlightjs.org/)

![](https://user-images.githubusercontent.com/35720395/66453678-e7096c00-ea6d-11e9-8b9a-fc4242525858.png)

If you want to modify this and create your own theme, put the `./Resources` directory inside another directory and name it with the extension `.iatemplate` ie. `./TemplateName.iatemplate/Resources/…`

The directory structure of the template is the following:

```
.
└── Contents
    └── Resources
        ├── en.lproj
        ├── font
        └── style
            └── hljs_styles
```

The directory where all the themes are installed is:
`~/Library/Containers/pro.writer.mac/Data/Library/Application Support/iA Writer/Templates`

iA has a templates [page](https://ia.net/writer/templates) and a [repository](https://github.com/iainc/iA-Writer-Templates), but these seem to be a bit out of the date and don't work on the newer versions of the application.

___

**Code highlighting**

If you want to add code highlighting for your own template, add the following snippet into the meta section of `./Contents/Resources/document.html`

```
    <script>
        document.addEventListener("DOMContentLoaded", function(){
            document.body.addEventListener('ia-writer-change', function(event) {
                var codeBlocks = document.querySelectorAll('pre code');
                [].forEach.call(codeBlocks, function(codeBlock) {
                    hljs.highlightBlock(codeBlock);
                });
            });
        });
    </script>
```

Also add highlight.pack.js to `./Contents/Resources` and hljs_styles to `./Content/Resources/style/`
