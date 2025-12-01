---
title: X-SMTPAPI
excerpt: >-
  X - SMTPAPI is a method provided by Aurora SendCloud for developers to
  customize emails. Aurora  SendCloud will search for the header field with the
  **key** of `X-SMTPAPI`. If this header field is found, it will parse the
  **value** to change the way the email is processed. Developers can use this
  field when accessing via SMTP and API.
deprecated: false
hidden: false
metadata:
  robots: index
---
API access：

**`sub` personalized template variable allows each recipient to receive customized email content based on their specific replacement value.**

```
x_smtpapi = {
	"to": ["d@163.com", "i@163.com"],
	"sub": {
		"%name%": ["jack", "rose"],
		"%money%": ["199", "299"]
	}
}

params['xsmtpapi'] = simplejson.dumps(x_smtpapi)
```

**`pubsub` common template variable, all recipients receive the same replaced content**

```
x_smtpapi = {
    "to": ["d@163.com", "i@163.com"],
    "pubsub": {
        "%productName%": "华为手表",
        "%discountedPrice%": 1989.0,
        "%discount%": "8.5"
    }
}

#OR:
x_smtpapi = {
    "pubsub": {
        "%productName%": "华为手表",
        "%discountedPrice%": 1989.0,
        "%discount%": "8.5"
    }
}

params['xsmtpapi'] = simplejson.dumps(x_smtpapi)
```

Note: Pubsub has a higher priority than sub. If both Pubsub and sub are passed simultaneously, sub will be ignored.

SMTP access：

```
x_smtpapi = {
	"to": ["d@163.com", "i@163.com"],
	"sub": {
		"%name%": ["jack", "rose"],
		"%money%": ["199", "299"]
	}
}

#OR：
x_smtpapi = {
    "to": ["d@163.com", "i@163.com"],
    "pubsub": {
        "%productName%": "华为手表",
        "%discountedPrice%": 1989.0,
        "%discount%": "8.5"
    }
}

#Custom header
msg['SC-Custom-key1'] = "value1"; 
msg['SC-Custom-key2'] = "value2";

msg['X-SMTPAPI'] = Header(base64.b64encode(simplejson.dumps(x_smtpapi)))
```

```
The SMTP server will check the format of the header field with the key of X-SMTPAPI in the email. If it doesn't meet the above requirements, an xsmtpapi error will be reported.
It should be noted that:

1. When making an SMTP call, X-SMTPAPI must be the last header field. Otherwise, it may lead to an xsmtpapi error.
2. When making an SMTP call, X-SMTPAPI must be encapsulated in base64 encoding. Otherwise, after a successful SMTP request, it will be intercepted by SendCloud during delivery and judged as an invalid email - a worker:invalid XSMTP - API error.
3. When making an API call, simply pass in a JSON string without base64 encoding encapsulation.
4. The total length of X-SMTPAPI cannot exceed 1M.
5. If a customer wants the data from the WebHook to include information embedded in the email, they can add a custom header during SMTP sending. The Key should start with "SC-Custom-", and this Key:Value will be returned to the user through the WebHook. The Key:Value should be a string.
6. Pubsub has a higher priority than sub. If both Pubsub and sub are passed simultaneously, sub will be ignored.
```

The structure and use of the JSON string encapsulated by value are shown below :

**`to` Contains an array of recipient addresses to specify the recipients of the message**.

```

    {
        "to": ["ben@ifaxin.com", "joe@ifaxin.com"]
    }

```

**Attention**:

* `to` here will override the recipient parameter `to`
* The number of `to` recipients here cannot exceed 100

**`Sub` is an associative array** its `key` is a variable' and `value` is a 'replacement value array'

Usage explanation: each "variable" corresponds to a "replacement value array". When replacing the contents of e-mail, each "Recipient" replaces the value of "variable" with the corresponding value in the "replacement value array" according to its position in the "recipient array"

Example :

```

# Email content

Dear %name%:

    Hello! Your consumption amount in ifaxin this month : %money% .

#---------------------------------------------------

# X-SMTPAPI

{
"to": ["ben@ifaxin.com", "joe@ifaxin.com"],
"sub":
{
"%name%": ["Ben", "Joe"],
"%money%":[288, 497]
}
}

#---------------------------------------------------

# ben@ifaxin.com will receive:

Dear Ben:

    Hello! Your consumption amount in ifaxin this month: 288 .

#---------------------------------------------------

# joe@ifaxin.com will receive:

Dear Joe:

    Hello! Your consumption amount in ifaxin this month: 497 .


```

**`apps` Tracking items and switches during sending**
“apps” is an associative array that contains a set of app names (unsubscribe, open, click) and their settings. These settings will override the settings in the user's account. The `enable` parameter can only take effect when the tracking domain is successfully configured.

```

x_smtpapi =
{

    "to": ["xxx@qq.com"],
    "sub": {"%name%": ["Joe"]},
    "filters": {
    "subscription_tracking": { # Unsubscribe tracking
    "settings": { "enable": "1" }
    },
    "open_tracking": { # Open tracking
    "settings": { "enable": "1" }
    },
    "click_tracking": { # Click tracking
    "settings": { "enable": "1" }
    }
    }
}

```

**`page_id` The unsubscribe page specified during sending**

Explanation of usage:

* The "page_id" corresponds to the ID field of a specific unsubscribe page created under "Unsubscribe Settings" - "Unsubscribe Page" in the "Sending Settings" of the Aurora SendCloud console.
* Customers need to create an unsubscribe page in advance in the Aurora SendCloud console before they can set the "page_id" to the corresponding ID during sending.
* When sending, pass the parameter "page_id" and set the value to the ID of a certain unsubscribe page. At this time, both the unsubscribe link and the unsubscribe page will be in the configured language and style.
* The priority of passing the "page_id" parameter is higher than the default unsubscribe page setting corresponding to the API_USER during sending.
* An array form is supported to specify the unsubscribe page, and the number of elements in the array needs to be the same as the number of "to" in x_smtpapi. The position of the element in the array corresponds one - to - one with the position of each "recipient" in the "recipient array". If the number of elements in the array does not match the number of "to", the default "page_id" of the customer under this apiUser will be used instead.

Example :

```
x_smtpapi =
{
    "to": ["xxx@qq.com"],
    "sub":{"%name%": ["Joe"]},
    "settings": 
    {
        "unsubscribe": 
            {"page_id": 562}
    }
}

```

**`send_domain` The sending domain name specified during sending**

Explanation of usage:

* Contact the customer service to activate relevant permissions before using this extended field.
* The domain name passed as `send_domain` should be added in advance on the "Settings" - "Domains" page in the Aurora SendCloud account and configured to pass as required.
* Customers can use the same API_USER. By means of the `send_domain` field, they can make emails be sent from the domain name specified by the customer.
* If customers pass in the `send_domain` field when sending emails, the sending resources and settings configured for that domain name will be used for scheduling.
  See the following example:

```json

x_smtpapi = 

{
    "send_domain":"customer.domain.com"
}

```