# Beatport API PHP Class

A simple PHP class to query the Beatport API via Oauth, server side.

The use case is for a server to server context.

The class essentially just returns an array which you can then manipulate as you please.

This is originally based on the following people's work:

* [Beatport API PHP Class](https://github.com/moussaclarke/beatportapi) by [Moussa Clarke](https://github.com/moussaclarke) (I forked this repo as a starting point)
* [Beatport API Json Feed](https://github.com/fedegiust/Beatport-API-JSON-feed) by Federico Giust
* [Beatport OAuth Connect w/ PECL](https://groups.google.com/forum/#!topic/beatport-api/sEpZUJkaSdo) by Tim Brandwijk (Federico Giust's script was based on this one)
* [Beatport OAuth Connect w/ PEAR](https://groups.google.com/forum/#!topic/beatport-api/sEpZUJkaSdo) by Christian Kolloch (Also based on Tim Brandwijk's script)

## Aims

* Login and query the Beatport API
* Abstract away the OAuth pain
* Send back a simple array with the query results

## Requirements

* PHP 5.5+
* Beatport API Key and login details (You'll need to request those from Beatport)
* Guzzle 6 (via composer)

## Install

```
composer require mrpc/beatportapi
```

## Usage

```
use mrpc\BeatportApi;

// auth parameters
$parameters = [
  'consumer'=> 'CONSUMERKEY', // Your Beatport API Key
  'secret' => 'SECRETKEY', // Your Beatport Secret Key
  'login' => 'BEATPORTLOGIN', // Your Beatport Login Name
  'password' => 'BEATPORTPASSWORD' // Your Beatport Password
  ];

// query parameters
$query = [
  'facets' => 'labelId:xyz', // The filter type
  'method' => 'releases', // The Beatport API Method
  'perPage' => '150' // Number of results per page
  ];

$api = new BeatportApi ($parameters); // initialise
$response = $api->queryApi ($query); // run the query
print_r ($response); // do something with response

```

You can check the [Beatport API documentation](https://oauth-api.beatport.com/) for which queries you can make and which parameters are required, although they are currently untested much beyond the above example, and not everything is documented, so your mileage may vary.

## Disclaimer

Totally and utterly alpha, and likely to break at any point. Not guaranteed to work as intended in any way, so use at your own risk.

## Todo

* Store the tokens somewhere and re-use until expiry
* Get some sanity into the variable / method names
* Add some proper error catching / messaging
* Test and document other query types.

## Contribute

Would be cool to improve this, so feel free to submit bug reports, suggestions and pull requests. Can't guarantee I've got enough time to do very much though! Alternatively just fork it and make your own thing.

## License
[WFTPL](http://www.wtfpl.net/), insofar as those other guys are cool with that.

