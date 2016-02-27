## Mixed Content
*Origin Link: <https://developer.mozilla.org/en-US/docs/Security/MixedContent>*

If the HTTPS page includes content retrieved through regular, cleartext HTTP, then the connection is only partially encrypted: the unencrypted content is accessible to sniffers and can be modified by man-in-the-middle attackers.

### Types of Mixed Content

1. **Mixed passive/display content**  
	Mixed Passive/Display Content is content served over HTTP that is included in an HTTPS webpage. An attackers could replace resources(listed below) which served over HTTP to users . Attacker could also infer information about the user's activities by watching which images are served to the user through observing HTTP requests.
	* `<img>` (src attribute)
	* `<audio>` (src attribute)
	* `<video>` (src attribute)
	* `<object>`subresources. (when an `<object>` performs HTTP requests)

2.  **Mixed active content**  
	Mixed Active Content is content that has access to all or parts of the Document Object Model of the HTTPS page. Attacker can intercept the request for the HTTP content or rewrite the response to include malicious JavaScript code. Here is a list of types of HTTP requests are considered active content:
	* `<script>` (src attribute)
	* `<link>` (href attribute) (this includes CSS stylesheets)
	* `<iframe>` (src attribute)
	* XMLHttpRequest requests
	* All cases in CSS where a url value is used (@font-face, cursor, background-image, etc.)
	* `<object>` (data attribute)
	
The difference lies in the threat level of the worst case scenario if content is rewritten as part of a Man-In-The-Middle attack. In the case of passive content, the threat is low (webpage appears broken or with misleading content). In the case of active content, the threat can lead to phishing, sensitive data disclosure, redirection to malicious sites.

