---
layout: post
title:  "Testing 1234!"
date:   2020-03-02 14:50:10 +0000
categories: jekyll update java
---

In this exciting first post we will be looking at how well jekyll formats java!

Here is a code snippet:

{% highlight java %}
{
@Singleton
public class WalletClient {

  private static final Logger LOG = LoggerFactory.getLogger(WalletClient.class);
  private static final String BACKOFFICE_USER_URL = "/internal/party/";

  private final HttpClient httpClient;
  private final MbConfig mbConfig;

  @Inject
  public WalletClient(HttpClient httpClient, MbConfig mbConfig) {
    this.httpClient = httpClient;
    this.mbConfig = mbConfig;
  }

  public Promise<String> getParty(Long partyId) {

    URI uri = URI.create(StringUtils.join(mbConfig.getWalletUrl(), BACKOFFICE_USER_URL, partyId.toString()));

    LOG.debug("Attempting to retrieve user details for party [{}] url: {}", partyId, uri);

    return httpClient.get(uri)
      .map(ReceivedResponse::getBody)
      .map(TypedData::getText);
  }
}
}
{% endhighlight %}

I Hope it worked!

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
