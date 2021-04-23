# Finixio - Laravel/PHP tech test
## Intro

Thanks for your interest in Finixio! Our [Laravel](https://laravel.com/)/PHP technical interview process involves candidates doing an at-home (or at work, or at Costa) project to test your PHP/framework knowledge and problem solving abilities, while also giving you a chance to write code in a way that you find comfortable.

This test should take about **1 hour**. If you take less time, no problem! If you take more time, that's cool too but don't spend more than 2 hours working on this. Using Google/StackOverflow/whatever for help is allowed, but ultimately you should write and be able to justify every piece of the code being submitted.

Your solution should be shared on a public Github or Bitbucket repo showing all commit history.

## Task
1. **Service**  
Write a `CryptoCompareService` using the [repository pattern](https://designpatternsphp.readthedocs.io/en/latest/More/Repository/README.html) that retrieves the prices of the top 10 coins from the [free cryptocompare API](https://min-api.cryptocompare.com/documentation) and persists these to a database architecture (mysql, redis, file)
2. **Console Cmd**  
Write a console command that executes your service when called with `crypto:fetch`
3. **Endpoint**  
Write an endpoint that returns the latest prices in JSON when a user visits `/crypto`

Once you have completed this, please provide instructions as to how to execute your application.

For example, the instructions might be:
```bash
# install the libraries
composer install

# fetch the coins
php artisan crypto:fetch

# test the endpoint
curl --request GET 'http://127.0.0.1/crypto'

# run the tests
./bin/phpunit
```


### 1. Service Info
- You should write this service using modern design principles, for example, using Dependency Injection and the Service Layer pattern. This will allow swapping the cryptocompare.com api with another with minimal rewriting.
- You are encouraged to use [Guzzle](https://docs.guzzlephp.org/en/stable/) or similar.
- Your code should be clean and testable

### 2. Console Cmd
- As mentioned, your command should trigger when calling `crypto:fetch` e.g. `php artisan crypto:fetch`
- Your command should use [Dependency Injection](https://designpatternsphp.readthedocs.io/en/latest/Structural/DependencyInjection/README.html) to invoke your service

### 3. Endpoint info
- Your endpoint should respond with JSON to the following request: (Assuming your service is run on 127.0.0.1)
```
curl --request GET 'http://127.0.0.1/crypto'
```
- You should return the data in the following format:
```json
{
    "BTC": {
        "name": "BTC",
        "fullName": "Bitcoin",
        "currentPrice": 10610.98,
        "currentPriceFormatted": "$10,610.98",
        "openingPrice": 10600,
        "openingPriceFormatted": "$10,600.00",
        "priceIncrease": 10.98,
        "priceIncreaseFormatted": "$10.98",
        "priceIncreasePercentage": 0.104,
        "priceIncreasePercentageFormatted": "0.104%",
        "lastRetrievedAt": "2021-04-21 10:11:56"
    },
    "ETH": { /** snip... **/}
    /* other coins here */
}
```


## Requirements
- Use a framework like laravel **or** just the `composer` packages you want. The focus is on your code, not the libraries or frameworks you use
- Use a modern version of PHP with appropriate design patterns for your code (Dependency Injection, Inheritance etc)

## Bonus points
- Write tests to cover your work
- Use DTO's to provide consistent input/output from your Service
- Dockerise your application