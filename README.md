# GitHub REST API Tutorial

https://docs.github.com/en/rest/guides/getting-started-with-the-rest-api

## What does this API do?

The GitHub REST API provides developers access to GitHub data from within their application. With it developers can retrieve items such as user profiles, repositories, issues, etc. Developers are also given the power to create repositories, issues, comments, etc. as well.

## Authorization Tutorial

GitHub bars developers from certain API features such as creating items without proper authorization. GitHub allows for authorization through the use of personal tokens that are account specific. These tokens must have a title and expiration date associated with them to be registered.  
In order to get authorized, a user must

1. Login to / create a GitHub account
2. Navigate to "Settings"
3. Navigate to "Developer settings"
4. Navigate to "Personal access tokens"
5. Click "Generate new token"
6. Enter their GitHub account password when prompted
7. Specify the purpose of the token in the "Note" section, give it an expiration date in the "Expiration" section, and select the scope of privileges for the token in the "Select scopes" section
8. Click "Generate token"
9. Copy the generated key and save it to an environment variable in your application (probably as 'GITHUB_API_KEY')

## Code Examples in Laravel

The API returns data in JSON format

### Getting a user profile

```
Http::withToken(env('GITHUB_API_KEY'))
    ->get('https://api.github.com/users/{username}');
```

### Getting a user's followers

```
Http::withToken(env('GITHUB_API_KEY'))
    ->get('https://api.github.com/users/{username}/followers');
```

### Getting a user's following list

```
Http::withToken(env('GITHUB_API_KEY'))
    ->get('https://api.github.com/users/{username}/following');
```

### Get a user's public repositories

```
Http::withToken(env('GITHUB_API_KEY'))
    ->get('https://api.github.com/users/{username}/repos');
```

## JSON Responses

We will be using the user 'defunkt' for the purpose of this tutorial as they do in the GitHub API tutorial. I will also be limiting the response to a few items in each list for the sake of this tutorial not being too long.

### https://api.github.com/users/defunkt

```
// 20220408181247
// https://api.github.com/users/defunkt

{
  "login": "defunkt",
  "id": 2,
  "node_id": "MDQ6VXNlcjI=",
  "avatar_url": "https://avatars.githubusercontent.com/u/2?v=4",
  "gravatar_id": "",
  "url": "https://api.github.com/users/defunkt",
  "html_url": "https://github.com/defunkt",
  "followers_url": "https://api.github.com/users/defunkt/followers",
  "following_url": "https://api.github.com/users/defunkt/following{/other_user}",
  "gists_url": "https://api.github.com/users/defunkt/gists{/gist_id}",
  "starred_url": "https://api.github.com/users/defunkt/starred{/owner}{/repo}",
  "subscriptions_url": "https://api.github.com/users/defunkt/subscriptions",
  "organizations_url": "https://api.github.com/users/defunkt/orgs",
  "repos_url": "https://api.github.com/users/defunkt/repos",
  "events_url": "https://api.github.com/users/defunkt/events{/privacy}",
  "received_events_url": "https://api.github.com/users/defunkt/received_events",
  "type": "User",
  "site_admin": false,
  "name": "Chris Wanstrath",
  "company": null,
  "blog": "http://chriswanstrath.com/",
  "location": null,
  "email": null,
  "hireable": null,
  "bio": "🍔",
  "twitter_username": null,
  "public_repos": 107,
  "public_gists": 273,
  "followers": 21405,
  "following": 210,
  "created_at": "2007-10-20T05:24:19Z",
  "updated_at": "2022-03-29T01:48:36Z"
}
```

### https://api.github.com/users/defunkt/followers

```
// 20220408181338
// https://api.github.com/users/defunkt/followers

[
  {
    "login": "mojombo",
    "id": 1,
    "node_id": "MDQ6VXNlcjE=",
    "avatar_url": "https://avatars.githubusercontent.com/u/1?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/mojombo",
    "html_url": "https://github.com/mojombo",
    "followers_url": "https://api.github.com/users/mojombo/followers",
    "following_url": "https://api.github.com/users/mojombo/following{/other_user}",
    "gists_url": "https://api.github.com/users/mojombo/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/mojombo/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/mojombo/subscriptions",
    "organizations_url": "https://api.github.com/users/mojombo/orgs",
    "repos_url": "https://api.github.com/users/mojombo/repos",
    "events_url": "https://api.github.com/users/mojombo/events{/privacy}",
    "received_events_url": "https://api.github.com/users/mojombo/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "pjhyett",
    "id": 3,
    "node_id": "MDQ6VXNlcjM=",
    "avatar_url": "https://avatars.githubusercontent.com/u/3?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/pjhyett",
    "html_url": "https://github.com/pjhyett",
    "followers_url": "https://api.github.com/users/pjhyett/followers",
    "following_url": "https://api.github.com/users/pjhyett/following{/other_user}",
    "gists_url": "https://api.github.com/users/pjhyett/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/pjhyett/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/pjhyett/subscriptions",
    "organizations_url": "https://api.github.com/users/pjhyett/orgs",
    "repos_url": "https://api.github.com/users/pjhyett/repos",
    "events_url": "https://api.github.com/users/pjhyett/events{/privacy}",
    "received_events_url": "https://api.github.com/users/pjhyett/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "vanpelt",
    "id": 17,
    "node_id": "MDQ6VXNlcjE3",
    "avatar_url": "https://avatars.githubusercontent.com/u/17?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/vanpelt",
    "html_url": "https://github.com/vanpelt",
    "followers_url": "https://api.github.com/users/vanpelt/followers",
    "following_url": "https://api.github.com/users/vanpelt/following{/other_user}",
    "gists_url": "https://api.github.com/users/vanpelt/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/vanpelt/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/vanpelt/subscriptions",
    "organizations_url": "https://api.github.com/users/vanpelt/orgs",
    "repos_url": "https://api.github.com/users/vanpelt/repos",
    "events_url": "https://api.github.com/users/vanpelt/events{/privacy}",
    "received_events_url": "https://api.github.com/users/vanpelt/received_events",
    "type": "User",
    "site_admin": false
  }
]
```

### https://api.github.com/users/defunkt/following

```
// 20220408181411
// https://api.github.com/users/defunkt/following

[
  {
    "login": "mojombo",
    "id": 1,
    "node_id": "MDQ6VXNlcjE=",
    "avatar_url": "https://avatars.githubusercontent.com/u/1?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/mojombo",
    "html_url": "https://github.com/mojombo",
    "followers_url": "https://api.github.com/users/mojombo/followers",
    "following_url": "https://api.github.com/users/mojombo/following{/other_user}",
    "gists_url": "https://api.github.com/users/mojombo/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/mojombo/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/mojombo/subscriptions",
    "organizations_url": "https://api.github.com/users/mojombo/orgs",
    "repos_url": "https://api.github.com/users/mojombo/repos",
    "events_url": "https://api.github.com/users/mojombo/events{/privacy}",
    "received_events_url": "https://api.github.com/users/mojombo/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "pjhyett",
    "id": 3,
    "node_id": "MDQ6VXNlcjM=",
    "avatar_url": "https://avatars.githubusercontent.com/u/3?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/pjhyett",
    "html_url": "https://github.com/pjhyett",
    "followers_url": "https://api.github.com/users/pjhyett/followers",
    "following_url": "https://api.github.com/users/pjhyett/following{/other_user}",
    "gists_url": "https://api.github.com/users/pjhyett/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/pjhyett/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/pjhyett/subscriptions",
    "organizations_url": "https://api.github.com/users/pjhyett/orgs",
    "repos_url": "https://api.github.com/users/pjhyett/repos",
    "events_url": "https://api.github.com/users/pjhyett/events{/privacy}",
    "received_events_url": "https://api.github.com/users/pjhyett/received_events",
    "type": "User",
    "site_admin": false
  }
]
```

### https://api.github.com/users/defunkt/repos

```
// 20220408181455
// https://api.github.com/users/defunkt/repos

[
  {
    "id": 1861402,
    "node_id": "MDEwOlJlcG9zaXRvcnkxODYxNDAy",
    "name": "ace",
    "full_name": "defunkt/ace",
    "private": false,
    "owner": {
      "login": "defunkt",
      "id": 2,
      "node_id": "MDQ6VXNlcjI=",
      "avatar_url": "https://avatars.githubusercontent.com/u/2?v=4",
      "gravatar_id": "",
      "url": "https://api.github.com/users/defunkt",
      "html_url": "https://github.com/defunkt",
      "followers_url": "https://api.github.com/users/defunkt/followers",
      "following_url": "https://api.github.com/users/defunkt/following{/other_user}",
      "gists_url": "https://api.github.com/users/defunkt/gists{/gist_id}",
      "starred_url": "https://api.github.com/users/defunkt/starred{/owner}{/repo}",
      "subscriptions_url": "https://api.github.com/users/defunkt/subscriptions",
      "organizations_url": "https://api.github.com/users/defunkt/orgs",
      "repos_url": "https://api.github.com/users/defunkt/repos",
      "events_url": "https://api.github.com/users/defunkt/events{/privacy}",
      "received_events_url": "https://api.github.com/users/defunkt/received_events",
      "type": "User",
      "site_admin": false
    },
    "html_url": "https://github.com/defunkt/ace",
    "description": "Ajax.org Cloud9 Editor",
    "fork": true,
    "url": "https://api.github.com/repos/defunkt/ace",
    "forks_url": "https://api.github.com/repos/defunkt/ace/forks",
    "keys_url": "https://api.github.com/repos/defunkt/ace/keys{/key_id}",
    "collaborators_url": "https://api.github.com/repos/defunkt/ace/collaborators{/collaborator}",
    "teams_url": "https://api.github.com/repos/defunkt/ace/teams",
    "hooks_url": "https://api.github.com/repos/defunkt/ace/hooks",
    "issue_events_url": "https://api.github.com/repos/defunkt/ace/issues/events{/number}",
    "events_url": "https://api.github.com/repos/defunkt/ace/events",
    "assignees_url": "https://api.github.com/repos/defunkt/ace/assignees{/user}",
    "branches_url": "https://api.github.com/repos/defunkt/ace/branches{/branch}",
    "tags_url": "https://api.github.com/repos/defunkt/ace/tags",
    "blobs_url": "https://api.github.com/repos/defunkt/ace/git/blobs{/sha}",
    "git_tags_url": "https://api.github.com/repos/defunkt/ace/git/tags{/sha}",
    "git_refs_url": "https://api.github.com/repos/defunkt/ace/git/refs{/sha}",
    "trees_url": "https://api.github.com/repos/defunkt/ace/git/trees{/sha}",
    "statuses_url": "https://api.github.com/repos/defunkt/ace/statuses/{sha}",
    "languages_url": "https://api.github.com/repos/defunkt/ace/languages",
    "stargazers_url": "https://api.github.com/repos/defunkt/ace/stargazers",
    "contributors_url": "https://api.github.com/repos/defunkt/ace/contributors",
    "subscribers_url": "https://api.github.com/repos/defunkt/ace/subscribers",
    "subscription_url": "https://api.github.com/repos/defunkt/ace/subscription",
    "commits_url": "https://api.github.com/repos/defunkt/ace/commits{/sha}",
    "git_commits_url": "https://api.github.com/repos/defunkt/ace/git/commits{/sha}",
    "comments_url": "https://api.github.com/repos/defunkt/ace/comments{/number}",
    "issue_comment_url": "https://api.github.com/repos/defunkt/ace/issues/comments{/number}",
    "contents_url": "https://api.github.com/repos/defunkt/ace/contents/{+path}",
    "compare_url": "https://api.github.com/repos/defunkt/ace/compare/{base}...{head}",
    "merges_url": "https://api.github.com/repos/defunkt/ace/merges",
    "archive_url": "https://api.github.com/repos/defunkt/ace/{archive_format}{/ref}",
    "downloads_url": "https://api.github.com/repos/defunkt/ace/downloads",
    "issues_url": "https://api.github.com/repos/defunkt/ace/issues{/number}",
    "pulls_url": "https://api.github.com/repos/defunkt/ace/pulls{/number}",
    "milestones_url": "https://api.github.com/repos/defunkt/ace/milestones{/number}",
    "notifications_url": "https://api.github.com/repos/defunkt/ace/notifications{?since,all,participating}",
    "labels_url": "https://api.github.com/repos/defunkt/ace/labels{/name}",
    "releases_url": "https://api.github.com/repos/defunkt/ace/releases{/id}",
    "deployments_url": "https://api.github.com/repos/defunkt/ace/deployments",
    "created_at": "2011-06-07T18:41:40Z",
    "updated_at": "2022-02-13T21:24:30Z",
    "pushed_at": "2011-11-16T18:37:42Z",
    "git_url": "git://github.com/defunkt/ace.git",
    "ssh_url": "git@github.com:defunkt/ace.git",
    "clone_url": "https://github.com/defunkt/ace.git",
    "svn_url": "https://github.com/defunkt/ace",
    "homepage": "http://ace.ajax.org",
    "size": 4405,
    "stargazers_count": 16,
    "watchers_count": 16,
    "language": "JavaScript",
    "has_issues": false,
    "has_projects": true,
    "has_downloads": true,
    "has_wiki": true,
    "has_pages": false,
    "forks_count": 7,
    "mirror_url": null,
    "archived": false,
    "disabled": false,
    "open_issues_count": 0,
    "license": {
      "key": "other",
      "name": "Other",
      "spdx_id": "NOASSERTION",
      "url": null,
      "node_id": "MDc6TGljZW5zZTA="
    },
    "allow_forking": true,
    "is_template": false,
    "topics": [

    ],
    "visibility": "public",
    "forks": 7,
    "open_issues": 0,
    "watchers": 16,
    "default_branch": "master"
  }
]
```
