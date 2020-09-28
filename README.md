# API Description

* The API provided by esignon is in the format of Header-Body.
* Body data format is also provided in Header-Body format for protocol code and version management.
* Format eg\) Header-Body \(Header-Body\)
* For some APIs, the body type may be different, so please refer to the description of each API.
* When using eSignon API, a unique client ID is required.
* For client ID issuance, please contact customer inquiry in our [homepage](https://esignon.net/en/customer/).
* How to use\) Client ID issuance \(customer inquiry\) -&gt; Authentication token issuance -&gt; API use by authentication token
* ※Please follow the format of header token value input※

## Ex\) Header

![](.gitbook/assets/head.png)

In the case of Header, up to 2 input values are received, and all APIs except for the token issuance API must request by entering a token value in the Authorization field. A space between esignon and token value must be entered.

## Ex\) Body

```jsx
{
    "header": {
        Key : "value"
    },
    "body": {
        key : "value"
    }
}
```

In the case of body, as above, when requesting, the header value and the key and value of the body must be written and requested in the body. Examples of key and value entered are listed in each API.

