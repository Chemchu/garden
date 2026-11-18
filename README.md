# Gus' digital garden

The posts and settings behind my website. The site itself is built by the
[garden-engine](https://github.com/Chemchu/garden-engine) engine, which this repository runs
as a Docker image.

| Path         | What it is                                               |
| ------------ | -------------------------------------------------------- |
| `garden/`    | The posts. `garden/welcome.md` is the home page.         |
| `site.toml`  | Name, links, colors, fonts, corner radius and sections.  |
| `assets/`    | Fonts and other static files, served under `/_static/`.  |
| `Dockerfile` | The engine version, and how the content goes into it.    |
| `fly.toml`   | The Fly.io app it deploys to.                            |

- Pull requests run the Check workflow, which builds the site and runs
  `garden-engine check`.
- Pushes to `main` check the content again and deploy it.
- Settings changed at `/admin` arrive as pull requests from the Site settings
  workflow.

Preview locally:

```sh
docker build -t garden .
docker run --rm garden ./garden-engine check
docker run --rm -p 3000:3000 garden
```

Want your own garden? Start from the
[template](https://github.com/Chemchu/garden-engine/tree/main/starter) instead of
forking this repository.
