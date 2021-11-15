# Fetch data

Fetch is the retrieval of data by a software program, script, or hardware device. After being retrieved, the data is moved to an alternate location or displayed on a screen.

## Fetch in python

In Python we have a module, called Requests, to make http requests extremely easily.

The module Requests is available on PyPI, to install it run from the terminal :

```
python -m pip install requests
```

## How to use Requests

To use the module Requests in your program, we need first to import it at the top of the file:

```py
import requests
```

Then we can use Requests, followed by the type of the request (get, post, put, delete ...) and inside the parentesis the url
of the resource from where we want to fetch the data.

```py
response = requests.get('https://randomuser.me/api/')
```

If we try to print response 

```py
response = requests.get('https://randomuser.me/api/')
print(response)
```

we will get the following output:

```
<Response [200]>
```

In order to be able to manipulate the data coming from the response we can convert it to a json format, using the json module.
The json module, like the Requests module, has to be imported:

```py
import requests
import json
```

Now we can use it with the module Requests:

```py
response = requests.get('https://randomuser.me/api/').json()
print(response)
```