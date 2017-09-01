# Schlepp

[![CircleCI](https://circleci.com/gh/TheGnarCo/schlepp/tree/master.svg?style=svg)](https://circleci.com/gh/TheGnarCo/schlepp/tree/master)

[![Coverage Status](https://coveralls.io/repos/github/TheGnarCo/schlepp/badge.svg?branch=master)](https://coveralls.io/github/TheGnarCo/schlepp?branch=master)

API client used for making authenticated JSON requests using a JWT bearer token to a
specified endpoint. Unauthenticated requests are also supported.

## Setup

Create an instance of Schlepp passing in your API host

```js
import Schlepp from 'schlepp';

const api = new Schlepp('https://example.com');
```

Set the bearer token for use in authenticated requests

```js
import Schlepp from 'schlepp';

const api = new Schlepp('https://example.com');

api.setBearerToken('my-bearer-token');
```

## Usage

Use the `authenticated` and `unauthenticated` objects to send an HTTP request to
the server. Both objects expose the same HTTP method functions (`get`, `delete`,
`post`, `patch`).

The difference between the `authenticated` and `unauthenticated` request is that the `authenticated` requests include an `Authorization` header: (`{ Authorization: 'Bearer my-bearer-token' }`).

## Examples

### Unauthenticated requests

```js
import Schlepp from 'schlepp';

const api = new Schlepp('https://example.com');

api.unauthenticated.get('posts?title=Unicorns');
api.unauthenticated.delete('users/1');
api.unauthenticated.post('users', { first_name: 'Charlie', last_name: 'Brown' });
api.unauthenticated.patch('users/1', { last_name: 'Chaplin' });
```

### Authenticated requests

```js
import Schlepp from 'schlepp';

const api = new Schlepp('https://example.com');

api.setBearerToken('my-bearer-token');

api.authenticated.get('posts?title=Unicorns');
api.authenticated.delete('users/1');
api.authenticated.post('users', { first_name: 'Charlie', last_name: 'Brown' });
api.authenticated.patch('users/1', { last_name: 'Chaplin' });
```
