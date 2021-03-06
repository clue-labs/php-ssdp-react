# clue/ssdp-react [![Build Status](https://travis-ci.org/clue/php-ssdp-react.svg?branch=master)](https://travis-ci.org/clue/php-ssdp-react)

Async [Simple Service Discovery Protocol (SSDP)](http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol), built on top of [React PHP](http://reactphp.org/).

As used in [Univeral Plug and Play](http://de.wikipedia.org/wiki/Universal_Plug_and_Play) (UPnP).
Commonly used by multimedia devices in home networks etc.

See [UPnP device architecture definition](http://upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf) (PDF).
Uses Multicast and Unicast UDP HTTP messages (HTTPMU/HTTPU),
expired IETF draft: https://tools.ietf.org/html/draft-goland-http-udp-01

This is an alternative to DNS-Based Service Discovery (DNS-SD)
as defined in [RFC 6763](http://tools.ietf.org/html/rfc6763).

> Note: This project is in early alpha stage! Feel free to report any issues you encounter.

## Quickstart example

Once [installed](#install), you can use the following code to search all available UPnP devices in your network:

```php
$loop = React\EventLoop\Factory::create();
$client = new Client($loop);

$client->search()->then(
    function () {
        echo 'Search completed' . PHP_EOL;
    },
    function($e) {
        echo 'There was an error searching for devices: ' . $e . PHP_EOL;
    },
    function ($progress) {
        echo 'Found a device: ' . PHP_EOL;
        var_dump($progress);
        echo PHP_EOL;
    }
);

$loop->run();
```

See also the [examples](examples).

## Install

The recommended way to install this library is [through composer](http://getcomposer.org). [New to composer?](http://getcomposer.org/doc/00-intro.md)

```JSON
{
    "require": {
        "clue/ssdp-react": "dev-master"
    }
}
```

## License

MIT
