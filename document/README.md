# Document directory
Your dissertation will live here. To get started simply replace the `main.tex` file or, if you started already (maybe in [Overleaf](https://www.overleaf.com/)), just copy the contents of your project and make sure the main document's name is `main.tex` (optionally, change the name in the [action workflow](../.github/workflows/build-and-publish-document.yml) to use a different name in the `Compile LaTeX document` step). From Overleaf you can download the project as a zip file and extract it here. You might need to add some LaTeX packages in the DevContainer's environment; you can do so by adding the packages to DevContainer's configuration file ([`devcontainer.json`](../.devcontainer/devcontainer.json)) under `features.ghcr.io/prulloac/devcontainer-features/latex:1.package`(persist through container recreations) or by using the command line inside the DevContainer with `tlmgr install <package_name>` (need to be added every time the container is rebuilt). 

If you are compiling more than one file make sure to add them to the action in the `Compile LaTeX document` step, to save the outputs as artifacts and to add them to the release to have the compiled pdfs available in the GitHub repository. 

## If you came here from [FEUP](https://sigarra.up.pt/feup/en/web_page.Inicial)
If you are a student at FEUP, you can unzip the template provided by the Dissertation Planning course unit or get the [template available in Overleaf](https://www.overleaf.com/latex/templates/feup-dissertation-format/qrsrxjjwzrzf) by opening it and downloading it as a zip file. See some documentation from the [creator](https://sigarra.up.pt/feup/pt/func_geral.formview?p_codigo=230756) himself [here](https://web.fe.up.pt/~jlopes/doku.php/teach/feupteses).

## Bibliography management recommendations
Throughout your dissertation it is important to manage the bibliography. There are many fully featured bibliography managers available, capable of exporting to LaTeX supported formats, (including open-source ones, like [Zotero](https://www.zotero.org/)), but I was seeking for something simpler that would use a simple file, something like a frontend for BibTex or biblatex. I ended up using [JabRef](https://www.jabref.org/), that uses the either of the formats and implements its features using comments to store all the necessary metadata. It has a browser extension for adding entries to the database and a lot of other features. JabRef can enrich your entries with data metadata from the web, query online aggregators and even search for the pdf files or metadata of your entries. You also can link your bibliography entries to the pdf files in the [`../research`](../research) directory and it will open them in your default pdf viewer. I recommend it. The best thing is that you can include the file directly in your LaTeX documents and start citing away.  