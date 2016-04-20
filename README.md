# Github.swift

[![CI Status](http://img.shields.io/travis/onmyway133/GithubSwift.svg?style=flat)](https://travis-ci.org/onmyway133/GithubSwift)
[![Version](https://img.shields.io/cocoapods/v/GithubSwift.svg?style=flat)](http://cocoadocs.org/docsets/GithubSwift)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![License](https://img.shields.io/cocoapods/l/GithubSwift.svg?style=flat)](http://cocoadocs.org/docsets/GithubSwift)
[![Platform](https://img.shields.io/cocoapods/p/GithubSwift.svg?style=flat)](http://cocoadocs.org/docsets/GithubSwift)

## Description

- A Swift implementation of [octokit.objc](https://github.com/octokit/octokit.objc), using [RxSwift](https://github.com/ReactiveX/RxSwift) and [Tailor](https://github.com/zenangst/Tailor)
- Hope it is useful to you, as it is to me
- Try to use more Swift style

## Usage

- User: identify a user
- Server: identify server (Github or Github Enterprise)
- Client: make request. If associated with a valid token, it is considered authenticated client

```swift
let user = User(rawLogin: "onmyway133", server: Server.dotComServer)
let client = Client(unauthenticatedUser: user)

client.fetchUserStarredRepositories().subscribeNext { repositories in
  print(repositories)
}
```

Make your own request using `RequestDescriptor`

```swift
let requestDescriptor = RequestDescriptor().then {
  $0.path = "repos/\(owner)/\(name)"
  $0.etag = "12345"  
}

return enqueue(requestDescriptor).map {
  return Parser.one($0.jsonArray)
}
```

## Features

#### Metadata

- Fetch server metadata

#### Sign in

- Native flow
- OAuth flow

#### User

- Follow
- Unfollow
- Fetch user info

#### Repository

- Fetch repositories
- Create repository
- Fetch commits
- Fetch pull requests
- Fetch issues
- Watch

#### Pull request

- Make pull requests

#### Organization (in progress)

- Fetch organizations
- Fetch teams

#### Search

- Search repositories

#### Event (in progress)

- Fetch user events

#### Gists (in progress)

- Fetch gists

#### Git (in progress)

- Create tree
- Create blob
- Create commit

#### Activity (in progress)

- Star
- Unstar

#### Notification

- Fetch notifications

## Installation

**GithubSwift** is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'Github.swift'
```

**GithubSwift** is also available through [Carthage](https://github.com/Carthage/Carthage).
To install just write into your Cartfile:

```ruby
github "onmyway133/Github.swift"
```

## Author

Khoa Pham, onmyway133@gmail.com

## Contributing

We would love you to contribute to **GithubSwift**, check the [CONTRIBUTING](https://github.com/onmyway133/GithubSwift/blob/master/CONTRIBUTING.md) file for more info.

## License

**GithubSwift** is available under the MIT license. See the [LICENSE](https://github.com/onmyway133/GithubSwift/blob/master/LICENSE.md) file for more info.
