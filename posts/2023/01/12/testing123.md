# Publishing from GitHub to Medium (Testing 123)

> This post was published from GitHub to Medium.
>
> The content of this post was scaffolded with the help of ChatGPT

Publishing posts from GitHub to Medium is a great way to share your technical content with a broader audience. By connecting your GitHub repository to Medium, you can automatically publish your posts to the platform and reach a larger audience.

To get started, you will need to create an account on Medium if you don't have one already. Click on your account icon and go to **Manage publications**

![image](https://user-images.githubusercontent.com/6097630/212096645-f74c1b0d-031b-4a3e-b9ca-9dea42a405a7.png)

Click on the **New publication** button and proceed to create your publication.

Once you have a publication, you can connect your GitHub repository to Medium by using a GitHub Action. This will allow you to publish your posts automatically every time you push a new commit to your repository.

The GitHub Action I'll be using is [Post to Medium Action](https://github.com/marketplace/actions/post-to-medium-action).

In the root directory of the repo that would be holding your blog posts, create the file `.github/workflows/post-to-medium.yaml`. Its content is shown below.

```yaml
name: post-to-medium

on:
  push:
    branches:
      - main

jobs:
  post-to-medium:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - name: Create Medium Post
        uses: philips-software/post-to-medium-action@v0.4.1
        with:
          integration_token: "${{ secrets.MEDIUM_ACCESS_TOKEN }}"
          file: "posts/2023/01/12/testing123.md" # insert your own path here
          content_format: "markdown"
          notify_followers: "false"
          tags: "test,github,medium"
          title: "Publishing from GitHub to Medium"
          license: "all-rights-reserved" # see https://github.com/marketplace/actions/post-to-medium-action for other options
          publish_status: "public" # see https://github.com/marketplace/actions/post-to-medium-action for other options
          publication_name: "${{ secrets.MEDIUM_PUBLICATION_NAME }}"
```

You can create a Medium access token as a value for the GitHub secret `MEDIUM_ACCESS_TOKEN` [here](https://medium.com/me/settings). Under the `Security and apps` tab click on `Integration tokens` to bring up the pop-up dialog where you create your access token.

The value of the secret `MEDIUM_PUBLICATION_TOKEN` is the name of the publication to which you wish to publish your posts.

Once you have set everything up, every time you push a new commit to the `main` branch of your GitHub repository, the GitHub Action will automatically publish the new post to Medium. This will save you a lot of time and effort, and make it easy to share your technical content with a wider audience.

In conclusion, publishing posts from Github to Medium is a great way to share your technical content with a broader audience. By connecting your GitHub repository to Medium using Medium API and GitHub Action, you can automate publishing your posts to Medium and reach a larger audience.
