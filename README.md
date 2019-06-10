## About it

The converter library is a `inmutable` drop in currencies converter that does not have concerns were a given currency value came from. 

In order for it to work, you will have to pass your repository data look up to pull in a valid information to operate on. This repository has to implement the interface `CurrenciesRepositoryInterface` [shipped](https://github.com/gocanto/converter/blob/master/src/Interfaces/CurrenciesRepositoryInterface.php) with the library  


## Working on your interface implementation

First of all, you will have to create a repository to query either your database or any other data resources where you keep your application currencies information. [see example](https://github.com/gocanto/converter/blob/master/src/Examples/CurrenciesRepositoryExample.php)

Second of all, you will have to new up the converter passing an instance of the mentioned interface repository implementation. Like so:

```php
use Gocanto\Converter\Examples\CurrenciesRepositoryExample;
use Gocanto\Converter\Converter;

$repository = new CurrenciesRepositoryExample;
$converter = new Converter($repository);
```
> Note: You can bind this interface within your app service container to have automatic dependencies injection resolution.

Lastly, you just need to invoke the required methods within the converter object to set the proper values for a given currency conversion (currency from, currency to). Like so:

```php
use Gocanto\Converter\RoundedNumber;

$conversion = $converter
    ->withAmount(RoundedNumber::make(10))
    ->withCurrency('SGD')
    ->convertTo('USD');
```

> This operation will return a Currency Conversion object that holds all the related operations info 

## Contributing

Please feel free to fork this package and contribute by submitting a pull request to enhance its functionalities.

## License

The MIT License (MIT). Please see [License File](https://github.com/gocanto/converter/blob/master/LICENSE.md) for more information.


## How can I thank you?
Why not star the github repo and share the link for this repository on Twitter?


Don't forget to [follow me on twitter](https://twitter.com/gocanto)!

Thanks!

Gustavo Ocanto.

