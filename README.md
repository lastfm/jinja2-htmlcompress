jinja2-htmlcompress
===================

Jinja2 extension that removes whitespace between HTML tags.
You can install this package from PyPi:
```bash
pip install j2hc
```
or GitHub:
```bash
pip install git+https://github.com/erthalion/jinja2-htmlcompress
```
 
Example usage:
```py
env = Environment(extensions=['j2hc.compressors.HTMLCompress'])
```
or for the coffin users:
```py
JINJA2_EXTENSIONS = [
    'j2hc.compressors.HTMLCompress'
]
```
How does it work? It throws away all whitespace between HTML tags
it can find at runtime. It will however preserve pre, textarea, style
and script tags because this kinda makes sense. There is one exception for script tags,
that contain an angularjs template:
```html
<script type="test/ng-template" ....
```
In order to force whitespace you can use ``{{ " " }}``.

Unlike filters that work at template runtime, this remotes whitespace
at compile time and does not add an overhead in template execution.

What if you only want to selective strip stuff?
```py
env = Environment(extensions=['j2hc.compressors.SelectiveHTMLCompress'])
```
And then mark blocks with:
```
{% strip %} ... {% endstrip %}
```
