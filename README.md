# Dissertation repository template
> A template repository for dissertations.

If your dissertation is already reaching the compilation limits of [Overleaf](https://www.overleaf.com/), you are overly paranoid about you data safety/security, you want to use `git` for version management or you simply want to have a local copy of your dissertation, ready to use with your favourite editor and tools, this template is for you.

## Desiderata
- [x] DevContainers [Open-Source specification](https://containers.dev/) / [VSCode docs](https://code.visualstudio.com/docs/devcontainers/containers) environment for [LaTeX](https://en.wikipedia.org/wiki/LaTeX) development with [VSCode](https://code.visualstudio.com/) and the [LaTeX Workshop extension](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
- [x] [GitHub Actions](https://github.com/features/actions) to build the document and publish it as an artifacts or release.

## Directory structure
```bash
dissertation-template/
├─ .devcontainer/                          # DevContainer configuration
│  ├─ devcontainer.json                    # DevContainer configuration file
├─ .github/                                # GitHub Actions configuration
│  ├─ workflows/                           # GitHub Actions workflows
│  │  ├─ build-and-publish-document.yml    
├─ document/                               # Document and bibliography
├─ logbook/                                # Logs of meetings and progresss
├─ research/                               # Research papers
```

Further explanation of the directory structure can be found inside the `README.md` files in each directory.s

## Requirements to use DevContainers
- [Docker](https://www.docker.com/)
- [VSCode](https://code.visualstudio.com/)
- [VSCode Remote development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

The first time you open the project in VSCode, you will be prompted to reopen the project in a container. If you miss this prompt, you can always reopen the project in a container by clicking the green icon in the bottom left corner of the VSCode window.

This configuration uses [prulloac](https://github.com/prulloac)'s [DevContainer feature](https://github.com/prulloac/devcontainer-features/tree/main/src/latex) in a [Debian](https://www.debian.org/) container. The feature installs [TeXLive](https://www.tug.org/texlive/) small scheme and the LaTeX Workshop extension. Some other packages are added to the container to make the development experience more pleasant:
- `texdoc`
- `collection-latexrecommended`
- `collection-fontsrecommended`
- `courier-scaled`
- `nextpage`
- `enumitem`
- `epigraph`
- `cleveref`

Other latex packages can be installed by adding them to the `packages` array in the `devcontainer.json` file or by running `tlmgr install <package>` in the container.

## State of the GitHub Actions workflow
### Build and publish document
- Triggers if a push is made modifying the `document/` directory
- Builds the document and stores it as an artifact (inside a zip file 😔)
- If the push is in the main branch it replaces the tag `latest` and its release with the updated document and commit. The document pdf is one of the assets of the release.
