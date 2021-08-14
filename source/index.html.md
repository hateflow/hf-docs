---
title: HateFlow API Reference

language_tabs: # must be one of https://git.io/vQNgJ

- shell
- python
- javascript

toc_footers:

- <a href='https://t.me/Jakob_Schoedl'>Sign Up for a Developer Key</a>
- <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:

- errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the HateFlow API documentation! Our REST API can help you to cope with all sorts of toxic comments on your
web page, app or whatever you need it for.

This site contains code samples for Shell, Python and JavaScript. You can view code examples in the dark area to the
right, and you can switch the programming language of the examples with the tabs in the top right.

<aside class="notice">Up to now, HateFlow is in beta and an official pricing scheme yet to be designed. Feel free
to contact us in order to get an API key. </aside>
<aside class="warning">The URL, methods and parameters can and will change in
the future. </aside>

# Toxicity Checks

## simpleCheck

****
> This sample checks the example text 'This is a nice comment.'

```shell
curl "http://api.hateflow.de/simpleCheck?text=This%20is%20a%20nice%20comment."
```

```python
import requests
import json

# The URL could change in the future - make sure to keep it replaceable.
API_URL = "http://api.hateflow.de/apis/neseps/"

comment_text = "This is a nice comment."
response = requests.get(f"{API_URL}simpleCheck?text={comment_text}")
if response.status_code != 200:
    print("Something went wrong!")
else:
    data = json.loads(response.text)
    print(data)
```

```javascript
const ApiRequest = async (text) => {
    const response = await fetch("http://api.hateflow.de/simpleCheck?text=" + text);
    const myJson = await response.json();
        // do something with the JSON data ('myJson')
    }
ApiRequest("This is a nice comment.");
```

> The server returns the following JSON as response.

```json
{
  "errors": [
    []
  ],
  "results": {
    "identity_hate": 0.0,
    "insult": 0.0,
    "obscene": 0.0,
    "severe_toxic": 0.0,
    "threat": 0.0,
    "toxic": 0.0
  },
  "warnings": [
    []
  ]
}
```

The sent comment is checked for all different attributes using Machine Learning.

Parameter | Default | Description
--------- | ------- | -----------
text      |         | The text (e.g. of a comment) to be checked
probabilities | ```0```   | If 0, use the thresholds to determine whether an attribute is true (values ```0.0``` or ```1.0```). Otherwise, use the raw output values returned by the classifiers (float between 0 and 1).
thresholds | ```{'identity_hate': 0.011,'insult': 0.062,'obscene': 0.099,'severe_toxic': 0.011,'threat': 0.008,'toxic': 0.104}``` | Thresholds to classify the attributes if ```probabilities``` is set to ```0```. Labels that are not given will be taken from the default thresholds.
