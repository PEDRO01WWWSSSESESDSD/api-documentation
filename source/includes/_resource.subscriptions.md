<!-- ___SUBSCRIPTIONS____________________________ -->
<h2 class="is-api head-3 margin-top-large margin-bottom-medium" id="subscriptions">Subscriptions</h2>

<section class="text-2 contain">
  <p>A subscription let's customers purchase monthly or yearly reocurring access to a sellers content. A subscription has many videos organized via playlists.</p>
</section>

<h3 class="text-2 text--navy text--bold is-api margin-top-large margin-bottom-medium" id="subscriptions-get">Get a Subscription</h3>

> <h5 class="head-5 text--white margin-bottom-medium">Create a subscription</h5>

> Definiton

```
GET /subscriptions/:id
```

> Example Request

```shell
$ curl -X GET "https://api.vhx.tv/subscriptions/:id" \
  -H "Authorization: Bearer <access_token>"
```

> Example Response

```json
{
  "_links": {
    "self":      { "href": "https://api.vhx.tv/subscriptions/1" },
    "site":      { "href": "https://api.vhx.tv/sites/1" },
    "buy_page":  { "href": "https://mymovie.vhx.tv/buy/subscription" }
  },
  "_embedded": {
    "site":    {},
    "trailer": {}
  },
  "id": 1,
  "title": "Subscription NOW",
  "description": "My subscription description.",
  "sku": "subscription",
  "price": {
    "cents": 500,
    "currency": "USD",
    "formatted": "$5",
    "monthly": {
      "cents": 500,
      "currency": "USD",
      "formatted": "$5"
    },
    "yearly": {
      "cents": 5000,
      "currency": "USD",
      "formatted": "$50"
    }
  },
  "trailer_url": "https://www.youtube.com/watch?v=dINgx0y4GqM",
  "thumbnail": {
    "small": "https://cdn.vhx.tv/assets/thumbnails/default-small.png",
    "medium": "https://cdn.vhx.tv/assets/thumbnails/default-medium.png",
    "large": "https://cdn.vhx.tv/assets/thumbnails/default-large.png",
    "blurred": null
  },
  "is_active": true,
  "playlists_count": 5,
  "videos_count": 30,
  "created_at": "2014-02-25T20:19:30Z",
  "updated_at": "2014-02-25T20:19:30Z"
}
```

<section class="text-2 contain margin-bottom-medium">
  <p>Retrieves an existing subscription and its associated collections (videos tied to it). <!-- You only need to request or supply the UUID that was returned upon subscription creation. --></p>
</section>

<table>
  <thead>
    <tr class="text-2">
      <th class="padding-medium nowrap">Arguments</th>
      <th class="padding-medium" width="100%">Description</th>
    </tr>
  </thead>

  <tbody>
    <tr class="text-2 border-bottom border--light-gray">
      <td class="nowrap">
        <strong class="is-block text--navy">subscription</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the subscription.</td>
    </tr>
  </tbody>
</table>