# Setup Private CocoaPods Repo

### Summary
First create a private spec repository, then setup local cocoapods installation, lastly one-liner change to Podfile.

### Steps
1. Create a private spec repo at `SOURCE_URL`

2. Add your prviate spec repo to your CocoaPods installation:
```ruby
pod repo add REPO_NAME SOURCE_URL
```
Now you can check the private spec repo at `~/.cocoapods/repos/REPO_NAME`.

3. Lint your podspec before push it to private spec repo:
```ruby
pod spec lint SPEC_NAME.podspec --verbose --allow-warnings
```

4. Push your podspec to private spec repo:
```ruby
pod repo push REPO_NAME SPEC_NAME.podspec --verbose --allow-warnings
```

5. Add `source` directive in your Podfile:
```ruby
source 'SOURCE_URL'
```
---
Reference:
- [Private Pods documentation](https://guides.cocoapods.org/making/private-cocoapods.html) from more information
- CocoaPods Guide - Command Line Reference [`pod spec lint`](https://guides.cocoapods.org/terminal/commands.html#pod_spec_lint)
- CocoaPods Guide - Command Line Reference [`pod repo push`](https://guides.cocoapods.org/terminal/commands.html#pod_repo_push)
