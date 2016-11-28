/*
# Literate Markdown

A tiny little function to extract code from [Fenced Code Blocks][2] in 
[Markdown][1] documents.

Inspired by [Literate Programming][3].

_Fun fact_: This README file is the actual source code for this module, 
and is parseable / executable javascript. Apologies for the weird comment 
artifacts, a few tricks with multiline comments were used.

_Fun fact #2_: This module is not javascript specific, although it is
implemented in javascript. You can embed _any_ language in your code
blocks.

## Implementation

This is the regular expression used to extract the contents of fenced 
code blocks:

``` javascript
/**/
var re = /^```[ \t]*\w+?\s*\n\s*([\w\W]+?)\s*(?:\n```)/gm;
/*
```

Here's the actual implementation of the extraction:

``` javascript
/**/
function extractFencedCodeBlocks(src) {
    if (typeof this.cacheable === 'function')
      this.cacheable(); // Allow for use as a webpack-loader
      
    const blocks = [];
    let match = null;
    while (match = re.exec(src)) {
      blocks.push(match[1]);
    }
    return blocks.join('\n\n');   
};

module.exports = extractFencedCodeBlocks;

/*
```

As mentioned above, it's quite tiny :)

[1]: https://daringfireball.net/projects/markdown/
[2]: https://help.github.com/articles/creating-and-highlighting-code-blocks/#fenced-code-blocks
[3]: https://en.wikipedia.org/wiki/Literate_programming
*/