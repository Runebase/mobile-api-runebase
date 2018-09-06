# RUNEBASE URIs
Represents a RUNEBASE payment URI. RUNEBASE URI strings became the most popular way to share payment request, sometimes as a RUNEBASE link and others using a QR code.

URI Examples:

```
runebase:12A1MyfXbW6RhdRAZEqofac5jCQQjwEPBu
runebase:12A1MyfXbW6RhdRAZEqofac5jCQQjwEPBu?amount=1.2
runebase:12A1MyfXbW6RhdRAZEqofac5jCQQjwEPBu?amount=1.2&message=Payment&label=Satoshi&extra=other-param
```

## URI Validation
The main use that we expect you'll have for the `URI` class in runebasecore is validating and parsing runebase URIs. A `URI` instance exposes the address as a runebasecore `Address` object and the amount in Satoshis, if present.

The code for validating URIs looks like this:

```javascript
var uriString = 'runebase:12A1MyfXbW6RhdRAZEqofac5jCQQjwEPBu?amount=1.2';
var valid = URI.isValid(uriString);
var uri = new URI(uriString);
console.log(uri.address.network, uri.amount); // 'livenet', 120000000
```

## URI Parameters
All standard parameters can be found as members of the `URI` instance. However a RUNEBASE URI may contain other non-standard parameters, all those can be found under the `extra` namespace.

## Create URI
Another important use case for the `URI` class is creating a RUNEBASE URI for sharing a payment request. That can be accomplished by using a dictionary to create an instance of URI.

The code for creating an URI from an Object looks like this:

```javascript
var uriString = new URI({
  address: '12A1MyfXbW6RhdRAZEqofac5jCQQjwEPBu',
  amount : 10000, // in satoshis
  message: 'My payment request'
});
var uriString = uri.toString();
```
