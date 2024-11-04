# Learn FastHTML

Visit [FastHTML](https://fastht.ml).

## Install
First, start by installing it.
> pip install python-fasthtml

## Usage

Create a `main.py` file.

```python
from fasthtml.common import *

app, rt = fast_app(live=True)

@rt('/')
def get():
  return Div(P('Hello world!'), hx_get="/change")

serve()
```

Then, you can run `python main.py` to host a local server with the app.

## HTMX

What it does is removes some constraints off the web browser, and it takes HTTP requests and does stuff with them.

## Create links

Lets a create a page that we can navigate.

```python
from fasthtml.common import *

app, rt = fast_app(live=True)

@rt('/')
def get():
  return Titled('Greeting',
    Div(P('Hello world!')),
    P(A('Link', href='/change'))
  )

@rt('/change')
def get():
  return Titled('Change',
    Div(P('Change is great!')),
    P(A('Home', href='/'))
  )
serve()
```

