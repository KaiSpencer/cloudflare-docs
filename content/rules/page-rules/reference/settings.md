---
pcx_content_type: reference
source: https://support.cloudflare.com/hc/en-us/articles/218411427-What-do-the-custom-caching-options-mean-in-Page-Rules-#summary-of-page-rules-settings
title: Settings
layout: wide
meta:
  title: Settings | Page Rules
weight: 3
---

# Page Rules settings

Settings control the action Cloudflare takes once a request matches the URL pattern defined in a page rule. You can use settings to enable and disable multiple Cloudflare features across the dashboard. Note that:

- Some settings require a Pro, Business, or Enterprise domain plan.
- You can specify more than one setting to apply when the rule triggers.

Below is the full list of settings available, presented in the order that they appear in the **Cloudflare Page Rules** page in the Cloudflare dashboard.

| **Setting** | **Description** | **Plans** |
| --- | --- | --- |
| [Always Use HTTPS](/ssl/edge-certificates/additional-options/always-use-https/) | Enable **Always Use HTTPS** feature. If enabled, any `http://` URL is converted to `https://` through a 301 redirect.<br/><br/>If this option does not appear, you do not have an active **Edge Certificate**. | All |
| [Auto Minify](/speed/optimization/content/auto-minify/) | Indicate which file extensions to minify automatically.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| [Automatic HTTPS Rewrites](/ssl/edge-certificates/additional-options/automatic-https-rewrites/) | Turn on or off **Automatic HTTPS Rewrites**.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| [Browser Cache TTL](/cache/how-to/edge-browser-cache-ttl/) | Control how long resources cached by client browsers remain valid. The Cloudflare dashboard and the API both prohibit setting **Browser Cache TTL** to `0` for non-Enterprise domains. | All |
| [Browser Integrity Check](/waf/tools/browser-integrity-check/) | Inspect the visitor's browser for headers commonly associated with spammers and certain bots.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| Bypass Cache on Cookie | Bypass cache and fetch resources from the origin server if a regular expression matches against a cookie name present in the request.<br/>If you add both this setting and the _Cache On Cookie_ setting to the same page rule, _Cache On Cookie_ takes precedence over _Bypass Cache on Cookie_.<br/><br/>Refer to the [Additional details](/rules/page-rules/reference/additional-reference/#bypass-cache-on-cookie-setting) to learn about limited regular expression support. | Business and Enterprise |
| [Cache By Device Type](/cache/how-to/edge-browser-cache-ttl/create-page-rules/#cache-by-device-type-enterprise-only) | Separate cached content based on the visitor’s device type.  | Enterprise |
| [Cache Deception Armor](/cache/cache-security/cache-deception-armor/) | Protect from web cache deception attacks while still allowing static assets to be cached. This setting verifies that the URL's extension matches the returned _Content-Type_. | All |
| [Cache Key](/cache/how-to/cache-keys/) | Also referred to as _Custom Cache Key_.<br/>Control specifically what variables to include when deciding which resources to cache. This allows customers to determine what to cache based on something other than just the URL. | Enterprise |
| Cache Level | Apply custom caching based on the option selected:<br/><br/>– **Bypass**: Cloudflare does not cache.<br/>– **No Query String**: Delivers resources from cache when there is no query string.<br/>– **Ignore Query String**: Delivers the same resource to everyone independent of the query string.<br/>– **Standard**: Caches all static content that has a query string.<br/>– **Cache Everything**: Treats all content as static and caches all file types beyond the [Cloudflare default cached content](/cache/concepts/default-cache-behavior/#default-cached-file-extensions). Respects cache headers from the origin web server unless **Edge Cache TTL** is also set in the Page Rule. When combined with an **Edge Cache TTL** > `0`, **Cache Everything** removes cookies from the origin web server response. | All |
| Cache on Cookie | Apply the _Cache Everything_ option (_Cache Level_ setting) based on a regular expression match against a cookie name.<br/>If you add both this setting and _Bypass Cache on Cookie_ to the same page rule, _Cache On Cookie_ takes precedence over _Bypass Cache on Cookie_. |  Business and above |
| [Cache TTL by Status Code](/cache/how-to/configure-cache-status-code/) | Enterprise customers can set cache time-to-live (TTL) based on the response status from the origin web server. Cache TTL refers to the duration of a resource in the Cloudflare network before being marked as stale or discarded from cache. Status codes are returned by a resource's origin. Setting cache TTL based on response status overrides the default cache behavior (standard caching) for static files and overrides cache instructions sent by the origin web server. To cache non-static assets, set a Cache Level of Cache Everything using a Page Rule. Setting no-store Cache-Control or a low TTL (using `max-age`/`s-maxage`) increases requests to origin web servers and decreases performance. | Enterprise |
| Disable Apps | Turn off all active **Cloudflare Apps**.<br>Note: This setting will not disable [Apps with Workers](https://cloudflareapps.com/apps/developer/docs/workers). These apps request permission to add a Worker when you are installing them. {{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| Disable Performance | Turn off [Auto Minify](/speed/optimization/content/auto-minify/), [Rocket Loader](/speed/optimization/content/rocket-loader/), [Mirage](/speed/optimization/images/mirage/), and [Polish](/images/polish/). | All |
| Disable Security| Turn off [Email Obfuscation](/waf/tools/scrape-shield/email-address-obfuscation/), [Rate Limiting (previous version)](/waf/reference/legacy/old-rate-limiting/), [Scrape Shield](/waf/tools/scrape-shield/), [Server Side Excludes](/waf/tools/scrape-shield/server-side-excludes/), [URL (Zone) Lockdown](/waf/tools/zone-lockdown/), and [WAF managed rules (previous version)](/waf/reference/legacy/old-waf-managed-rules/). | All |
| Disable Zaraz | Turn off [Zaraz](/zaraz/).{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| Edge Cache TTL | Specify how long to cache a resource in the Cloudflare global network. _Edge Cache TTL_ is not visible in response headers. | All |
| [Email Obfuscation](/waf/tools/scrape-shield/email-address-obfuscation/) | Turn on or off **Email Obfuscation**.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| Forwarding URL | Redirects one URL to another using an `HTTP 301/302` redirect. Refer to [Wildcard matching and referencing](/rules/page-rules/reference/wildcard-matching/). | All |
| [Host Header Override](/rules/page-rules/how-to/rewrite-host-headers/) | Apply a specific host header.{{<render file="_origin-rule-promotion.md" productFolder="rules" withParameters="/rules/origin-rules/features/#host-header">}} | Enterprise |
| IP Geolocation Header | Cloudflare adds a `CF-IPCountry` HTTP header containing the country code that corresponds to the visitor. {{<Aside type="note">}}You can accomplish the same effect with the [**Add visitor location headers** Managed Transform](/rules/transform/managed-transforms/reference/#add-visitor-location-headers).{{</Aside>}} | All |
| [Mirage](/speed/optimization/images/mirage/) | Turn on or off **Mirage**.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | Pro and above |
| [Opportunistic Encryption](/ssl/edge-certificates/additional-options/opportunistic-encryption/) | Turn on or off the **Opportunistic Encryption**.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| [Origin Cache Control](/cache/concepts/cache-control/) | Origin Cache Control is enabled by default for Free, Pro, and Business domains and disabled by default for Enterprise domains. |  All |
| Origin Error Page Pass-thru | Turn on or off Cloudflare error pages generated from issues sent from the origin server. If enabled, this setting triggers error pages issued by the origin. | Enterprise |
| [Polish](/images/polish/) | Apply options from the **Polish** feature of the Cloudflare **Speed** app.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | Pro and above |
| [Query String Sort](/cache/advanced-configuration/query-string-sort/) | Turn on or off the reordering of query strings. When query strings have the same structure, caching improves. | Enterprise |
| [Resolve Override](/rules/page-rules/how-to/override-url-or-ip-address/) | Change the origin address to the value specified in this setting. {{<render file="_origin-rule-promotion.md" productFolder="rules" withParameters="/rules/origin-rules/features/#dns-record">}}| Enterprise |
| [Respect Strong ETags](/cache/reference/etag-headers/) | Turn on or off byte-for-byte equivalency checks between the Cloudflare cache and the origin server. | Enterprise |
| Response Buffering | Turn on or off whether Cloudflare should wait for an entire file from the origin server before forwarding it to the site visitor. By default, Cloudflare sends packets to the client as they arrive from the origin server. |  Enterprise |
| [Rocket Loader](/speed/optimization/content/rocket-loader/) | Turn on or off **Rocket Loader** in the Cloudflare **Speed** app.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| [Security Level](/waf/tools/security-level/) | Control options for the **Security Level** feature from the **Security** app. {{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| [Server Side Excludes](/waf/tools/scrape-shield/server-side-excludes/)| Turn on or off the **Server Side Excludes** feature of the Cloudflare **Scrape Shield** app.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} |  All |
| [SSL](/ssl/origin-configuration/ssl-modes/) | Control options for the **SSL** feature of the **Edge Certificates** tab in the Cloudflare **SSL/TLS** app.{{<render file="_configuration-rule-promotion.md" productFolder="rules">}} | All |
| True Client IP Header | Turn on or off the [**True-Client-IP Header**](/network/true-client-ip-header/) feature of the Cloudflare **Network** app. | Enterprise |
| Web Application Firewall | Turn on or off [WAF managed rules (previous version)](/waf/reference/legacy/old-waf-managed-rules/).<br/>You cannot enable or disable individual WAF managed rules via Page Rules. | Pro and above |