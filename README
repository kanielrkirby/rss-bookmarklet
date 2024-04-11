# RSS Bookmarklet

Just a small bookmarklet for copying various site's RSS URLs to your clipboard.

![Drag and Drop to Your Bookmarks!](javascript:(function() { function copy(link) { navigator.clipboard.writeText(link) .then(() => alert(`Copied: ${link}`)) .catch((e) => alert(`Failed to copy: ${e}`)) } if (document.location.hostname.match(/.*stackoverflow.com.*/) && document.location.pathname.match(/\/questions\/\d+.*/)) { let link = `${document.location.hostname}/feeds/question/${document.location.pathname.split("/")[2]}`; copy(link); return; } if (document.location.hostname.match(/.*github.com.*/)) { if (document.location.pathname.match(/^\/[^/]*\/?$/)) { let pathname = document.location.pathname; pathname = pathname.replace(/\/$/, ''); let link = `https://${document.location.hostname}${pathname}.atom`; copy(link); return; } if (document.location.pathname.match(/^\/[^/]*\/[^/]*\/?$/)) { let pathname = document.location.pathname; pathname = pathname.replace(/\/?$/, ''); let link = `https://${document.location.hostname}${pathname}/commits.atom`; copy(link); return; } if (document.location.pathname.match(/^\/[^/]*\/[^/]*\/releases\/?$/)) { let pathname = document.location.pathname; pathname = pathname.replace(/\/?$/, ''); let link = `https://${document.location.hostname}${pathname}.atom`; copy(link); return; } } if (document.location.hostname.match(/.*reddit.com.*/)) { let href = document.location.href; href = href.replace(/\/$/, '').replace(/.*reddit.com\//, 'https://old.reddit.com/'); let link = `${href}/.rss`; copy(link); return; } if (document.location.hostname.match(/.*medium.com.*/)) { if (document.location.pathname.match(/^\/@[^/]*(\/.*)?\/?$/)) { let username = document.location.pathname.split("/")[1]; let link = `https://medium.com/feed/@${username}`; copy(link); return; } if (document.location.hostname.match(/.*\.medium.com\/?$/)) { let link = `${document.location.hostname}/feed/`; copy(link); return; } if (document.location.pathname.match(/^\/[^/]*(\/[^/]*)?\/?$/)) { let publication = document.location.pathname.split("/")[1]; let link = `https://medium.com/feed/${publication}`; copy(link); return; } if (document.location.pathname.match(/^\/[^/]*\/tagged\/.*\/?$/)) { let link = `https://${document.location.hostname}/feed${document.location.pathname}`; copy(link); return; } if (document.location.pathname.match(/^\/tag\/.*\/?$/)) { let link = `https://${document.location.hostname}/feed${document.location.pathname}`; copy(link); return; } } else if (document.querySelector('meta[property="og:site_name"][content="Medium"]')) { let link = `https://${document.location.hostname}/feed/`; copy(link); return; } /* Brute force check */ let searches = [ 'href$=".xml"', 'rel="alternate"', 'title="RSS"', 'type="application/rss+xml"' ]; let set = new Set(); for (let s in searches) { let results = [...document.querySelectorAll(`head link[${searches[s]}][href]`)]; for (let r of results) { console.log(r); if (r.href) { set.add(r.href); } } } let arr = Array.from(set); if (arr.length === 0) { alert('No RSS found'); return; } if (arr.length > 1) { alert('More than one potential RSS found. Logging them all, using first.'); for (var i = 0; i < arr.length; i++) { console.log(arr[i]); } } let href = `${arr[0]}`; copy(href); }());)

Supports the following sites officially, with extra-janky support for others. Your mileage may vary.

- GitHub
  - Releases - `/:user/:repo/releases`
  - Repository - `/:user/:repo`
  - Users - `/:user`
  - Organizations - `/:org`

- StackOverflow
  - Questions - `/questions/:id`

- Medium
  - Authors - `/@:author`
  - Subdomains - `:author.medium.com`
  - Custom domain - `:domain`
  - Tags - `/tagged/:tag` and `:blog/tagged/:tag`

- Reddit
  - Subreddits - `/r/:subreddit`
  - Users - `/user/:user`
  - Threads - `/comments/:id`
  - Posts - `/comments/:id`

- YouTube
  - Channels

If you want to contribute, please feel free!
