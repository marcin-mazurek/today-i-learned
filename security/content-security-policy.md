# Content Security Policy

It's an HTTP header which helps to mitigate attacks like XSS or data injection. It allows to specify safe origins of scripts and assets to run/display on a page.

For example, the following header allows to execute scripts coming from the application domain only:
```
Content-Security-Policy: default-src 'self'
```

The header below allows scripts from the application domain and from `*.trusted.com`:

```
Content-Security-Policy: default-src 'self' *.trusted.com
```

The header allows to report violations to an API endpoint by adding a [`report-uri`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/report-uri) directive (which is being deprecated in favour of [`report-to`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/report-to) directive).

If you want to test a Content Security Policy without trigerring an error, you can specify a `Content-Security-Policy-Report-Only` header.
It accepts the same directives as the `Content-Security-Policy` tag, including `report-uri`.
