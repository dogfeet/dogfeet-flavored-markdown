
## Change Log

### 2012-08-03

#### Github code block convenstion

from:

    ```mylang
    mycode
    ```
to:

    <pre><code class="dfm mylang">mycode
    </code></pre>

#### Just multiline string

from:

    '''mylang
    mycode
    '''
to:

    <span class="dfm mylang">mycode
    </span>

### 2012-05-20

#### Support for `@mention`, `#hash`

Mention and Hash patterns are:

    mention - (^|[ \t]+)@([a-zA-Z0-9]+)
    hash - (^|[ \t]+)#([ㄱ-ㅎ가-힣a-zA-Z0-9]+) //include korean

You can implement your handlers:

    var templates={
      '@': function(key){ return ['@@', key].join(''); }
      , '#': function(key){ return ['##', key].join(''); }
    }
    var dfm = require("dogfeet-flavored-markdown");
    gfm.parse("I **love** @DFM. #DFM", {templates:templates});
    // returns:
    // '<p>I <strong>love</strong> @@DFM. ##DFM'

#### Remove implicit refercences

Remove implicit refercences from github-flavored-markdown like that:

    SHA: be6a8cc1c1ecfe9489fb51e4869af15a13fc2cd2
    User@SHA ref: mojombo@be6a8cc1c1ecfe9489fb51e4869af15a13fc2cd2
    #Num: #1
    User/#Num: mojombo#1

