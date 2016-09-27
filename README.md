# errorception

Quick and **dirty** extract of the [official script](https://errorception.com/docs) to be used as NPM module without polluting global space. There are no additional dependencies.

## Install

```bash
  npm install errorception
```

## Usage

```js
  import errorception from 'errorception';
  errorception.setup(-ProjectID-);
```

These two lines should be included in your code as soon as possible. Calling setup will actually attach `window.onerror` to report unhandled exceptions.

### Push

Official documentation: https://errorception.com/docs/push

```js
  errorception.push(error);
```

### Meta

Official documentation: https://errorception.com/docs/meta

```js
  const meta = {
    email: "email@domain.com",
    sessionId: 4138727492,
    lovesCats: true
  };

  errorception.setup(-ProjectID-, meta);
  // OR
  errorception.setMeta(meta);
  // OR
  errorception.push(error, meta);
```

Note that every type of call overwrites global meta for a whole module. Currently there is no way to specify meta for a single error report.

### Filtering

Official documentation: https://errorception.com/docs/allow

```js
  errorception.useFilter(function() {
    return (navigator.userAgent.indexOf("MSIE 6") == -1);
  });
```

Once again this is global per whole module.
