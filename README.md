# Github Top Issues

This utility allows you to see the top issues (as measured by # of interactions, priority labels, and age) in any Github repository's issue tracker.

You can view the [top issues for mapbox/mapbox-gl-js](https://mapbox.github.io/top-issues/#!mapbox/mapbox-gl-js) at

```
https://mapbox.github.io/top-issues/#!mapbox/mapbox-gl-js
```

To view the top issues for another repository, replace the repository name in the URL (everything after the `#!`).
```
https://mapbox.github.io/top-issues/#!OWNER/REPOSITORY
```

![screenshot](screenshot.png)

## Rate Limiting

Github API requests are rate limited by IP address. You can raise the rate limit by using a [personal Github access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/). To link a use an access token, append `github_username` and `github_access_token` parameters to the URL.
```
https://mapbox.github.io/top-issues/?github_username=USERNAME&github_access_token=ACCESS_TOKEN#!mapbox/mapbox-gl-js
```

## Private Repos

To use this tool with a private repo, append `github_username` and `github_access_token` parameters to the URL.
```
https://mapbox.github.io/top-issues/?github_username=USERNAME&github_access_token=ACCESS_TOKEN#!secret-agent/top-secret-stuff
```

## `.topissuesrc`

You can specify custom scoring settings for your repositry by creating a `.topissuesrc` file in the root directory. This file must be formatted as JSON.

```js
{
    "labels": {
        "high priority": 7,
        "medium priority": 5,
    },
    "reactions": {
        "+1": 1,
        "-1": -1,
        "laugh": 1,
        "hooray": 1,
        "confused": 1,
        "heart": 1
    }
}
```

The properties in the `labels` object assign a scores to labels. You may add as many labels as you like. You may use negative scores if you like. You do not need to assign a score to every label in your project. Because only repository collaborators may add labels, these scores represent the will of the collaborators. 

The properties in the `reactions` object assign scores to [Github reactions](https://github.com/blog/2119-add-reactions-to-pull-requests-issues-and-comments). Only reactions on the initial issue comment "count." Because anyone may add reactions, these scores represent the will of the community.
