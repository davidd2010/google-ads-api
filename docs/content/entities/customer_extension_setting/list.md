---
type: list
entity: CustomerExtensionSetting
title: List CustomerExtensionSetting
order: 3
---

This `customer.customerExtensionSettings.list()` method works just like `get`, except that it returns all of the entities in the account. It isn't rate limited, but it can be very slow, so use it sparingly.

```javascript
// Listing all the customerExtensionSettings in the account
let result = await customer.customerExtensionSettings.list()

// Listing with constraints and a limited number of results
let result = await customer.customerExtensionSettings.list({
    constraints: [
        {
            key: 'customer_extension_setting.some_field',
            op: '=',
            val: 'yellow submarine',
        },
    ],
    limit: 15,
})

// Here's what the result might look like
result ===
    [
        {
            customer: {
                resource_name: 'customers/9262111890',
                auto_tagging_enabled: false,
                call_reporting_setting: {
                    call_conversion_action: 'customers/9262111890/conversionActions/179',
                    call_conversion_reporting_enabled: true,
                },
                conversion_tracking_setting: { conversion_tracking_id: 797556569 },
                currency_code: 'EUR',
                descriptive_name: 'My customer',
                has_partners_badge: false,
                id: 9262111890,
                manager: false,
                remarketing_setting: {
                    google_global_site_tag:
                        "<!-- Global site tag (gtag.js) - Google Ads: 797556569 -->\n<script async src=\"https://www.googletagmanager.com/gtag/js?id=AW-797556569\"></script>\n<script>\n  window.dataLayer = window.dataLayer || [];\n  function gtag(){dataLayer.push(arguments);}\n  gtag('js', new Date());\n\n  gtag('config', 'AW-797556569');\n</script>\n",
                },
                test_account: true,
                time_zone: 'Europe/London',
            },
            customer_extension_setting: {
                resource_name: 'customers/9262111890/customerExtensionSettings/SITELINK',
                extension_feed_items: [{ value: 'customers/9262111890/extensionFeedItems/51840594005' }],
                extension_type: 10,
            },
        },
    ]
```