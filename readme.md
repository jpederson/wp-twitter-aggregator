## wp-twitter-aggregator

This script uses the [twitter-api-php](https://github.com/J7mbo/twitter-api-php) library to retrieve twitter feeds, aggregate them and cache them in the uploads folder of WordPress. It's designed to be included in your custom theme(s) so you can avoid using an additional plugin to handle this for you. It has caching so you only hit the twitter API every 10 minutes (or so - you can change the cache timeout). Enough ado, here's a sample integration.

#### Clone it:

```sh
// change to your theme directory
cd themes/my-theme

// clone the repo
git clone git@github.com:jpederson/wp-twitter-aggregator.git twitter-aggregator

// change into the aggregator directory and download its submodule
git submodule init
git submodule update
```

#### In `functions.php`:

```php
// this path can be updated to store the aggregator in any directory of your theme.
require_once( 'twitter-aggregator/widget.php' );
```

#### In your theme template file:

```php
// add your own key and oauth settings into this array
$aggregator_settings = array(
    'consumer_key' => "[CONSUMER KEY]",
    'consumer_secret' => "[CONSUMER SECRET]",
    'oauth_access_token' => "[OAUTH ACCESS TOKEN]",
    'oauth_access_token_secret' => "[OAUTH ACCESS TOKEN SECRET]",
    'usernames' => "[TWITTER USERNAME]",
    'limit' => "10"
);

// output the actual widget
twitter_aggregator_widget( $aggregator_settings );
```

Developed by [James Pederson](http://jpederson.com)