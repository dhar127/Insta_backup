
# Instaloader Usage Guide

Instaloader is a powerful tool for downloading Instagram pictures, videos, reels, and other metadata. This guide provides an overview of how to use Instaloader to download content from Instagram profiles.

## Table of Contents

- [Installation](#installation)
- [Basic Usage](#basic-usage)
- [Download Examples](#download-examples)
- [Login for Private Profiles](#login-for-private-profiles)
- [Advanced Features](#advanced-features)
- [Complete Python Script](#complete-python-script)
- [References](#references)

## Installation

To install Instaloader, use pip:

```bash
pip install instaloader
```

## Basic Usage

### Download a User's Profile

To download all posts from a user's profile:

```bash
instaloader profile <profile_name>
```

### Download a Single Post

To download a specific post by URL:

```bash
instaloader post <post_url>
```

## Download Examples

### Downloading Posts, Reels, and Videos Programmatically

You can also use Instaloader within a Python script to download content programmatically:

```python
import instaloader

# Create an instance of Instaloader
L = instaloader.Instaloader()

# Download a profile
profile_name = "profile_name"
profile = instaloader.Profile.from_username(L.context, profile_name)

# Iterate over posts and download
for post in profile.get_posts():
    L.download_post(post, target=profile_name)

    # Check if the post is a reel or video
    if post.typename == "GraphVideo":
        L.download_post(post, target=profile_name)
```

## Login for Private Profiles

To access private profiles, you need to login:

```python
L.login("your_username", "your_password")
```

You can save your session to avoid logging in every time:

```python
# Save session
L.context.log("your_username")

# Load session
L.load_session_from_file("your_username")
```

## Advanced Features

### Download Stories

To download stories of a profile:

```bash
instaloader --stories profile <profile_name>
```

### Download Hashtags

To download posts with a specific hashtag:

```bash
instaloader hashtag <hashtag_name>
```

## Complete Python Script

Here’s a complete example script that downloads posts, reels, and videos from a profile:

```python
import instaloader

# Create an instance of Instaloader
L = instaloader.Instaloader()

# Login (optional)
# L.login("your_username", "your_password")

# Define the profile to download
profile_name = "profile_name"

# Load the profile
profile = instaloader.Profile.from_username(L.context, profile_name)

# Iterate over posts
for post in profile.get_posts():
    # Download post
    L.download_post(post, target=profile_name)

    # Check if the post is a reel or video
    if post.typename == "GraphVideo":
        L.download_post(post, target=profile_name)
```

## References

- [Instaloader Documentation](https://instaloader.github.io/)
- [GitHub Repository](https://github.com/instaloader/instaloader)

Feel free to contribute to this project by submitting issues or pull requests.
```

This README provides a clear guide for using Instaloader, including installation, basic usage, programmatic downloading, and advanced features. It also includes a complete example script and references to further documentation.
