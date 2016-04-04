## Meta tags that Google understands

*Origin Link: <https://support.google.com/webmasters/answer/79812>*

Note:
* Google can read both **HTML** and **XHTML**-style meta tags, regardless of the code used on the page.
* With the exception of **verify**, case is generally not important in meta tags.

### Provide descriptive information

[HTML Improvements page](https://www.google.com/webmasters/tools/html-suggestions) shows you potential issues Google found when crawling and indexing your site. It will check these data:

* Title problems: potential problems with the title tag on your pages, such as missing or repeated page titles.
* Meta description problems: Potential problems with duplicate or otherwise problematic meta descriptions.
* Non-indexable content: pages containing non-indexable content, such as some rich media files, video, or images.

#### description

    <meta name="description" content="A description of the page" />

This tag provides a short description of the page. In some situations this description is used as a part of the snippet shown in the search results.

#### title

    <title>The Title of the Page</title>

The content of the title tag is generally shown as the title in search results (and of course in the user's browser).

### Robots meta tag

The list of google robots:

* Googlebot
* Googlebot-News(Googlebot)
* Googlebot-Image(Googlebot)
* Googlebot-Video(Googlebot)
* Googlebot-Mobile
* Mediapartners-Google / Mediapartners(Googlebot)
* AdsBot-Google

#### robots

    <meta name="robots" content="index, follow" />
    <meta name="googlebot" content="all" />

These meta tags can control the behavior of search engine crawling and indexing. The default values are "index, follow" (the same as "all") and do not need to be specified. Google understands the following values (when specifying multiple values, separate them with a comma):

* noindex: prevents the page from being indexed
* nofollow: prevents the crawler from following links from this page.

    Another similar usage is in anchor element:

        <a href="signin.php" rel="nofollow">sign in</a>
    
    "rel" attribute with value "nofollow" tell search engines and bots not to crawl the link. For getting other values, read <http://www.w3schools.com/tags/att_a_rel.asp>.

* nosnippet: prevents a snippet from being shown in the search results
* noodp: prevents the alternative description from the ODP/DMOZ from being used
* noarchive: prevents search engine from showing the cached link for a page.
* unavailable_after:[date]: lets you specify the exact time and date you want to stop crawling and indexing of this page
* noimageindex: lets you specify that you do not want your page to appear as the referring page for an image that appears in search results.
* none: is equivalent to noindex, nofollow.

### Google features

### google

Tell Google not to display search box of your site in search results:

    <meta name="google" content="nositelinkssearchbox" />

Searchbox screenshot:
![searchbox](../pictures/160227-searchbox.png)

Tell Google not to provide translation link of your site in search results:

    <meta name="google" content="notranslate" />

### google-site-verification

You can use this tag to verify ownership for Search Console:

    <meta name="google-site-verification" content="..." />

**[Here](https://support.google.com/webmasters/answer/35179)** get infos about verifing your site ownership.

### http-equiv

    <meta http-equiv="Content-Type" content="...; charset=..." />
    <meta charset="...">

These two meta tags define the page's content type and character set. Unicode/UTF-8 is recommended.

    <meta http-equiv="refresh" content="...;url=..." />

This meta tag sends the user to a new URL after a certain amount of time, and is sometimes used as a simple form of redirection. However, it is not supported by all browsers and can be confusing to the user. The W3C recommends that this tag not be used. Google recommend using a server-side 301 redirect instead.

