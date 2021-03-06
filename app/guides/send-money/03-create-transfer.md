---
layout: twoColumn
section: guides
type: guide
guide:
    name: send-money
    step: '3'
title:  "Step 3: Create a transfer"
---

# Step 3: Create a transfer

Create a [transfer](https://docsv2.dwolla.com/#transfers) by specifying your funding source as the **source** and the Customer or Account as the **destination**.

```raw
POST https://api-uat.dwolla.com/transfers
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q
{
    "_links": {
        "source": {
            "href": "https://api-uat.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
        },
        "destination": {
            "href": "https://api-uat.dwolla.com/customers/C7F300C0-F1EF-4151-9BBE-005005AC3747"
        }
    },
    "amount": {
        "currency": "USD",
        "value": "225.00"
    },
    "metadata": {
        "customerId": "8675309",
        "notes": "For work completed on Sept. 1, 2015"
    }
}

HTTP/1.1 201 Created
Location: https://api-uat.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
```
```ruby
transfer_request = {
  :_links => {
      :destination => {:href => 'https://api-uat.dwolla.com/customers/C7F300C0-F1EF-4151-9BBE-005005AC3747'},
      :source => {:href => 'https://api-uat.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985'}
  },
  :amount => {:currency => 'USD', :value => 225.00},
  :metadata => {
      :customerId => 8675309,
      :notes => 'For work completed on Sept. 1, 2015'
  }
}

xfer = DwollaSwagger::TransfersApi.create({:body => transfer_request})
p xfer # => https://api-uat.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
```
```javascript
dwolla.then(function(dwolla) {
    dwolla.transfers.create({
      "_links": {
          "destination": {
              "href": "https://api-uat.dwolla.com/customers/C7F300C0-F1EF-4151-9BBE-005005AC3747"
          },
          "source": {
              "href": "https://api-uat.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
          }
      },
      "amount": {
          "currency": "USD",
          "value": "225.00"
      },
      "metadata": {
          "customerId": "8675309",
          "notes": "For work completed on Sept. 1, 2015"
      }
      }).then(function(data) {
          console.log(data.obj); // https://api.dwolla.com/transfers/74c9129b-d14a-e511-80da-0aa34a9b2388
      })
})
```
```python
transfer_request = {
    "_links": {
        "source": {
            "href": "https://api-uat.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
        },
        "destination": {
            "href": "https://api-uat.dwolla.com/customers/C7F300C0-F1EF-4151-9BBE-005005AC3747"
        }
    },
    "amount": {
        "currency": "USD",
        "value": "225.00"
    },
    "metadata": {
        "customerId": "8675309",
        "notes": "For work completed on Sept. 1, 2015"
    }
}

transfers_api = dwollaswagger.TransfersApi(client)
xfer = transfers_api.create(body=transfer_request)

print(xfer) # => https://api-uat.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
```
```php
<?php
$transfer_request = array (
  '_links' => 
  array (
    'source' => 
    array (
      'href' => 'https://api-uat.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985',
    ),
    'destination' => 
    array (
      'href' => 'https://api-uat.dwolla.com/customers/C7F300C0-F1EF-4151-9BBE-005005AC3747',
    ),
  ),
  'amount' => 
  array (
    'currency' => 'USD',
    'value' => '225.00',
  ),
  'metadata' => 
  array (
    'customerId' => '8675309',
    'notes' => 'For work completed on Sept. 1, 2015',
  ),
);

$transferApi = new DwollaSwagger\TransfersApi($apiClient);
$myAccount = $transferApi->create($transfer_request);

print($xfer); # => https://api-uat.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
?>
```

<nav class="pager-nav">
    <a href="02-fetch-funding-sources.html">Back: Fetch funding sources</a>
    <a href="04-check-transfer.html">Next step: Check the transfer status</a>
</nav>