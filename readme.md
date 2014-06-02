# Zenbox (supports turbolinks)

zendesk supplies feedback tab.

[Setting up your Feedback Tab channel : Zendesk Support](https://support.zendesk.com/entries/20990726-Setting-up-your-Feedback-Tab-channel)

but it doesn't run collectly with turbolinks.

[rails/turbolinks](https://github.com/rails/turbolinks)

so I decided to create own zenbox.js

# Usage

1. copy "zenbox.js" into vendor/assets/javascripts
2. require zenbox.js from application.js

```
# = require zenbox.js
```

3. paste following lines into layouts/application.html

```
$(function(){
  window.zenbox_params = {
    dropboxID:   "your id",
    url:         "https://yourname.zendesk.com",
    tabTooltip:  "Support",
    tabImageURL: "https://p1.zdassets.com/external/zenbox/images/tab_ja_support.png",
    tabColor:    "black",
    tabPosition: "Left"
  }

  Zenbox.init(window.zenbox_params);
});
```

# Diffs from original

1. binding to 'page:load' not 'load'
2. window.Zenbox has an function nullifyTab

it nullifies an local variable named 'tab'. Zenbox.init creates elements if only !tab is true. So we must nullify tab before init.
