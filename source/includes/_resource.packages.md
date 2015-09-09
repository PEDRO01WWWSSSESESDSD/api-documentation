<!-- ___PACKAGES____________________________ -->
<h2 class="is-api head-3 margin-top-large margin-bottom-medium" id="packages">Packages</h2>

<section class="text-2 contain">
  <p>A package is the unit for sale via a site. A package has a price tag and has videos and bonus materials inside of it.</p>
</section>

<h3 class="text-2 text--navy text--bold margin-top-large margin-bottom-medium" id="packages-create">Create a Package</h3>

> <h5 class="head-5 text--white margin-bottom-medium">Create a Package</h5>

> Definiton

```
POST /packages
```

> Example Request

```shell
$ curl -X POST "https://api.vhx.tv/packages" \
  -H "Authorization: Bearer <access_token>" \
  -d title="My Package" \
  -d description="My package description." \
  -d price_cents=500 \
  -d trailer_url=https://www.youtube.com/watch?v=dINgx0y4GqM \
  -d custom_email_message="Thank you for buying my movie!" \
  -d is_preorder=true \
  -d release_date=2015-02-25 \
  -d site=https://api.vhx.tv/sites/1
```

> Example Response

```json
{
  "_links": {
    "self":     { "href": "https://api.vhx.tv/packages/1" },
    "site":     { "href": "https://api.vhx.tv/sites/1" },
    "buy_page": { "href": "https://mymovie.vhx.tv/buy/my-sku" }
  },
  "_embedded": {
    "site":   {},
    "videos": []
  },
  "id": 1,
  "title": "My Package",
  "description": "My package description.",
  "sku": "my-sku",
  "price": {
    "cents": 500,
    "currency": "USD",
    "formatted": "$5"
  },
  "rental": null,
  "trailer_url": "https://www.youtube.com/watch?v=dINgx0y4GqM",
  "thumbnail": {
    "small": "https://cdn.vhx.tv/assets/thumbnails/default-small.png",
    "medium": "https://cdn.vhx.tv/assets/thumbnails/default-medium.png",
    "large": "https://cdn.vhx.tv/assets/thumbnails/default-large.png",
    "blurred": null
  },
  "is_active": true,
  "is_preorder": false,
  "videos_count": 0,
  "extras_count": 0,
  "created_at": "2014-02-25T20:19:30Z",
  "updated_at": "2014-02-25T20:19:30Z"
}
```


<section class="text-2 contain margin-bottom-medium">

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
      <td>
        <strong class="is-block text--navy">title</strong>
        <span class="text--yellow text-3">REQUIRED</span>
        <span class="text--transparent text-3">string</span>
      </td>
      <td>The package title.</td>
    </tr>
    <!-- TODO this should be optional / pricing not always necessary via api -->
    <tr class="text-2 border-bottom border--light-gray">
      <td class="nowrap">
        <strong class="is-block text--navy">price_cents</strong>
        <span class="text--yellow text-3">REQUIRED</span>
        <span class="text--transparent text-3">integer</span>
      </td>
      <td>The price of the package in USD cents.</td>
    </tr>
    <tr class="text-2 border-bottom border--light-gray">
      <td class="nowrap">
        <strong class="is-block text--navy">trailer_url</strong>
        <span class="text--transparent text-3">optional string, default is null</span>
      </td>
      <td>A YouTube or Vimeo video url.</td>
    </tr>
  </tbody>
</table>

<h3 class="text-2 text--navy text--bold is-api margin-top-large margin-bottom-medium" id="packages-retrieve">Retrieve a Package</h3>

> <h5 class="head-5 text--white margin-bottom-medium">Retrieve a Package</h5>

> Definiton

```
GET /packages/:id
```

> Example Request

```shell
$ curl -X GET "https://api.vhx.tv/packages/:id" \
  -H "Authorization: Bearer <access_token>"
```

> Example Response

```json
{
  "_links": {
    "self":     { "href": "https://api.vhx.tv/packages/1" },
    "site":     { "href": "https://api.vhx.tv/sites/1" },
    "buy_page": { "href": "https://mymovie.vhx.tv/buy/my-sku" }
  },
  "_embedded": {
    "site":   {},
    "videos": []
  },
  "id": 1,
  "title": "My Package",
  "description": "My package description.",
  "sku": "my-sku",
  "price": {
    "cents": 500,
    "currency": "USD",
    "formatted": "$5",
    "GB": {
      "cents": 100,
      "currency": "GBP",
      "formatted": "£1"
    }
  },
  "rental": {
    "price": {
      "cents": 300,
      "currency": "USD",
      "formatted": "$3"
    },
    "period": 259200
  },
  "trailer_url": "https://www.youtube.com/watch?v=dINgx0y4GqM",
  "thumbnail": {
    "small": "https://cdn.vhx.tv/assets/thumbnails/default-small.png",
    "medium": "https://cdn.vhx.tv/assets/thumbnails/default-medium.png",
    "large": "https://cdn.vhx.tv/assets/thumbnails/default-large.png",
    "blurred": null
  },
  "is_active": true,
  "is_preorder": false,
  "release_date": 2014-03-17,
  "videos_count": 10,
  "extras_count": 0,
  "created_at": "2014-02-25T20:19:30Z",
  "updated_at": "2014-02-25T20:19:30Z"
}
```
<section class="text-2 contain">
  <p>Retrieves an existing package. Returns information for a package and the videos included in it. You only need to request or supply the UUID that was returned upon package creation.</p>
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
        <strong class="is-block text--navy">package</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the package.</td>
    </tr>
  </tbody>
</table>

<h3 class="text-2 text--navy text--bold margin-top-large margin-bottom-medium" id="packages-add">Add a Video</h3>

> <h5 class="head-5 text--white margin-bottom-medium">Add a Video to a Package</h5>

> Definiton

```
PUT /packages/:id/videos
```

> Example Request

```shell
$ curl -X PUT "https://api.vhx.tv/packages/:id/videos" \
  -H "Authorization: Bearer <access_token>" \
  -d video=https://api.vhx.tv/videos/1
```

> Example Response

```
Status: 204 No Content
```

<section class="text-2 contain">
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
      <td>
        <strong class="is-block text--navy">package</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the package.</td>
    </tr>
    <tr class="text-2 border-bottom border--light-gray">
      <td class="nowrap">
        <strong class="is-block text--navy">video</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the video to add.</td>
    </tr>
  </tbody>
</table>


<h3 class="text-2 text--navy text--bold margin-top-large margin-bottom-medium" id="packages-delete">Remove a Video</h3>

> <h5 class="head-5 text--white margin-bottom-medium">Remove a Video from a Package</h5>

> Definiton

```
DELETE /packages/:id/videos
```

> Example Request

```shell
$ curl -X DELETE "https://api.vhx.tv/packages/:id/videos" \
  -H "Authorization: Bearer <access_token>" \
  -d video=https://api.vhx.tv/videos/1
```

> Example Response

```
Status: 204 No Content
```

<section class="text-2 contain">
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
      <td>
        <strong class="is-block text--navy">package</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the package.</td>
    </tr>
    <tr class="text-2 border-bottom border--light-gray">
      <td class="nowrap">
        <strong class="is-block text--navy">video</strong>
        <span class="text--yellow text-3">REQUIRED</span>
      </td>
      <td>The UUID for the video to remove.</td>
    </tr>
  </tbody>
</table>