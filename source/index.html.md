---
title: PHP API Reference

toc_footers:
  - <a href='https://github.com/cloudipsp/'>GitHub Org</a>
includes:
  - checkout
  - order
  - p2pcredit
  - payment
  - subscription
  - pcidss
  - verification
  - result
  - errors

search: true
---

# Introduction

The CloudIPSP PHP SDK is an open source library through which your PHP application can easily interact with the API. That allows you to accept payment by Visa/MasterCard cards on your website. Simply generating payment url, token, form.

# Installation

1. You can install via Composer.

> 1.Composer Install

```cmd
composer require cloudipsp/php-sdk-v2
```

2. To install without composer, just download the latest release. Then include manual auto loader to your project.

> 2.Manual installation

```php
<?php
require '/path-to-sdk/autoload.php';
```

# Simple start

> Minimal startup example:

```php
<?php
require 'vendor/autoload.php';

\Cloudipsp\Configuration::setMerchantId(1396424);
\Cloudipsp\Configuration::setSecretKey('test');

$data = [
    'currency' => 'USD',
    'amount' => 1111
];
\Cloudipsp\Checkout::url($data)->toCheckout();
```

**Minimal configuration:**

* ```'setMerchantId'``` - Checkout Merchant ID from provider merchant portal.
* ```'setSecretKey'``` - Merchant secret key, if operation is credit you need to set ```'setCreditKey'```

**Full configuration:**

* ```'setMerchantId'``` - Checkout Merchant ID from provider merchant portal.
* ```'setSecretKey'``` - Merchant secret key.
* ```'setCreditKey'```- Merchant credit key.
* ```'setApiVersion'``` - Set api protocol version. Allowed ['1.0', '2.0'].
* ```'setApiUrl'``` - Set api endpoint.
* ```'setRequestType'``` - Set request type. Allowed ['json', 'xml', 'form'].
* ```'setHttpClient'``` - Set http client. Allowed HttpCurl, HttpGuzzle.

<aside class="notice">
<p class="nothing">
Protocol 2.0 allowed only json type. <br/>
The response is always returned in request context in the same content-type. So if a request is sent in JSON, response will be sent in JSON format too.</p>
</aside>



