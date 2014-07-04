# GitHub Cheat Sheet
Une collection de... cool hidden and not so hidden features of Git and GitHub. This cheat sheet was inspired by [Zach Holman](https://github.com/holman)'s [Git and GitHub Secrets](http://www.confreaks.com/videos/1229-aloharuby2012-git-and-github-secrets) talk at Aloha Ruby Conference 2012 ([slides](https://speakerdeck.com/holman/git-and-github-secrets)) and his [More Git and GitHub Secrets](https://vimeo.com/72955426) talk at WDCNZ 2013 ([slides](https://speakerdeck.com/holman/more-git-and-github-secrets)).

*Lien court: [`http://git.io/sheet`](http://git.io/sheet)*

*Lire ce document dans différentes langues: [English](README.md), [한국어](README.ko.md), [日本語](README.ja.md), [简体中文](README.zh-cn.md), [French](README.fr.md).*

## Table des matières
 - [GitHub](#github)
  - [Ignorer les espaces](#ignorer-les-espaces)
  - [Adjust Tab Space](#adjust-tab-space)
  - [Historique de commit by Author](#commit-historique-by-author)
  - [Cloning a Dépôt](#cloning-a-repository)
  - [Compare all Branches to Another Branch](#compare-all-branches-to-another-branch)
  - [Comparing Branches](#comparing-branches)
  - [Compare Branches across Forked Repositories](#compare-branches-across-forked-repositories)
  - [Gists](#gists)
  - [Git.io](#gitio)
  - [Keyboard Shortcuts](#keyboard-shortcuts)
  - [Line Highlighting in Repositories](#line-highlighting-in-repositories)
  - [Closing Issues via Commit Messages](#closing-issues-via-commit-messages)
  - [Cross-Link Issues](#cross-link-issues)
  - [CI Status on Pull Requests](#ci-status-on-pull-requests)
  - [Syntax Highlighting in Markdown Files](#syntax-highlighting-in-markdown-files)
  - [Emojis](#emojis)
  - [Images/GIFs](#imagesgifs)
    - [Embedding Images in GitHub Wiki](#embedding-images-in-github-wiki)
  - [Quick Quoting](#quick-quoting)
  - [Quick Licensing](#quick-licensing)
  - [Task Lists](#task-lists)
    - [Task Lists in Markdown Documents](#task-lists-in-markdown-documents)
  - [Relative Links](#relative-links)
  - [Metadata and Plugin Support for GitHub Pages](#metadata-and-plugin-support-for-github-pages)
  - [Viewing YAML Metadata in your Documents](#viewing-yaml-metadata-in-your-documents)
  - [Rendering Tabular Data](#rendering-tabular-data)
  - [Diffs](#diffs)
    - [Rendered prose Diffs](#rendered-prose-diffs)
    - [Diffable Maps](#diffable-maps)
    - [Expanding Context in Diffs](#expanding-context-in-diffs)
    - [Diff or Patch of Pull Request](#diff-or-patch-of-pull-request)
    - [Rendering and diffing images](#rendering-and-diffing-images)
  - [Hub](#hub)
  - [Decreasing Contributor Friction](#decreasing-contributor-friction)
  - [Contributing Guidelines](#contributing-guidelines)
  - [GitHub Resources](#github-resources)
    - [GitHub Talks](#github-talks)
 - [Git](#git)
  - [Previous Branch](#previous-branch)
  - [Stripspace](#stripspace)
  - [Checking out Pull Requests](#checking-out-pull-requests)
  - [Empty Commits :trollface:](#empty-commits-trollface)
  - [Styled Git Status](#styled-git-status)
  - [Styled Git Log](#styled-git-log)
  - [Git Query](#git-query)
  - [Merged Branches](#merged-branches)
  - [Web Server for Browsing Local Repositories](#web-server-for-browsing-local-repositories)
  - [Configurations Git](#configurations-git)
    - [Aliases](#les-alias)
    - [Auto-correction](#auto-correction)
    - [Couleur](#couleur)
  - [Ressources Git](#ressources-git)
    - [Livres Git](#livres-git)

## GitHub
### Ignorer les espaces
Ajouter `?w=1` à une URL de diff supprime les changements concernant uniquement les espaces, ce qui permet de voir uniquement le code qui a changé.

![Diff sans espace](https://camo.githubusercontent.com/797184940defadec00393e6559b835358a863eeb/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f626c6f672f323031312f736563726574732f776869746573706163652e706e67)

[*En savoir plus sur les secrets de GitHub.*](https://github.com/blog/967-github-secrets)

### Ajuster le caractère de tabulation (Tab Space)
Ajouter `?ts=4` à une URL de diff ou de fichier permet d'afficher les tabulations avec 4 espaces au lieu de 8 par défaut. Le nombre après le `ts` peut être ajusté selon vos préférences. This does not work on Gists, or raw file views.

Here is a Go source file [before](https://github.com/pengwynn/flint/blob/master/flint/flint.go) adding `?ts=4`:

![Before, tab space example](http://i.imgur.com/GIT1Fr0.png)

...and this is [after](https://github.com/pengwynn/flint/blob/master/flint/flint.go?ts=4) adding `?ts=4`:

![After, tab space example](http://i.imgur.com/70FL4H9.png)

### Historique de commit by Author
To view all commits on a repo by author add `?author=username` to the URL.

```
https://github.com/rails/rails/commits/master?author=dhh
```

![DHH commit historique](http://i.imgur.com/mDWwuaY.png)

[*En savoir plus about the differences between commits views.*](https://help.github.com/articles/differences-between-commit-views)

### Cloning a Dépôt
When cloning a repository the `.git` can be left off the end.

```bash
$ git clone https://github.com/tiimgreen/github-cheat-sheet
```

[*En savoir plus about the Git `clone` commande.*](http://git-scm.com/docs/git-clone)

### Compare all Branches to Another Branch

If you go to the repo's [Branches](https://github.com/tiimgreen/github-cheat-sheet/branches) page, next to the Commits button:

```
https://github.com/{user}/{repo}/branches
```

... you would see a list of all branches which are not merged into the main branch.

From here you can access the compare page or delete a branch with a click of a button.

![Compare branches not merged into master in jquery/jquery repo - https://github.com/jquery/jquery/branches](http://i.imgur.com/gKWPe8a.png)

However, often you need to compare branches to a branch other than `master` (e.g. `development`). To do this, append the URL with the name of the branch like so:

```
https://github.com/{user}/{repo}/branches/{branch}
```

![Compare branches not merged into `1.x-master` in jquery/jquery repo - https://github.com/jquery/jquery/branches/1.x-master](http://i.imgur.com/jpc6Urb.png)

To see the merged branches, append `?merged=1` to the URL.

![Compare branches merged in to `1.x-master` in jquery/jquery repo - https://github.com/jquery/jquery/branches/1.x-master?merged=1](http://i.imgur.com/KmYyCVh.png)

This view allows you to delete branches easily from the page, without using the commande-line.

### Comparing Branches
To use GitHub to compare branches, change the URL to look like this:

```
https://github.com/user/repo/compare/{range}
```

Where `{range} = master...4-1-stable`

Par exemple :

```
https://github.com/rails/rails/compare/master...4-1-stable
```

![Rails branch compare example](http://i.imgur.com/0Z52X5Y.png)

`{range}` can be changed to things like:

```
https://github.com/rails/rails/compare/master@{1.day.ago}...master
https://github.com/rails/rails/compare/master@{2014-10-04}...master
```

*Dates are in the format `YYYY-DD-MM`*

![Another compare example](http://i.imgur.com/5dtzESz.png)

...which allows you to see the difference on the master branch up a set time ago or a specified date.

[*En savoir plus about comparing commits across time.*](https://help.github.com/articles/comparing-commits-across-time)

### Compare Branches across Forked Repositories
To use GitHub to compare branches across forked repositories, change the URL to look like this:

```
https://github.com/user/repo/compare/{foreign-user}:{branch}...{own-branch}
```

Par exemple :

```
https://github.com/rails/rails/compare/byroot:master...master
```

![Forked branch compare](http://i.imgur.com/Q1W6qcB.png)

### Gists
[Gists](https://gist.github.com/) are an easy way to work with small bits of code without creating a fully fledged repository.

![Gist](http://i.imgur.com/VkKI1LC.png?1)

Add `.pibb` to the end of any Gist URL ([like this](https://gist.github.com/tiimgreen/10545817.pibb)) in order to get the *HTML only* version suitable for embedding in any other site.

Gists can be treated as a full repository so they can be cloned like any other:

```bash
$ git clone https://gist.github.com/tiimgreen/10545817
```

![Gists](http://i.imgur.com/dULZXXo.png)

[*En savoir plus about creating gists.*](https://help.github.com/articles/creating-gists)

### Git.io
[Git.io](http://git.io) is a simple URL shortener for GitHub.

![Git.io](http://i.imgur.com/6JUfbcG.png?1)

You can also use it via pure HTTP using Curl:

```bash
$ curl -i http://git.io -F "url=https://github.com/..."
HTTP/1.1 201 Created
Location: http://git.io/abc123

$ curl -i http://git.io/abc123
HTTP/1.1 302 Found
Location: https://github.com/...
```

[*En savoir plus about Git.io.*](https://github.com/blog/985-git-io-github-url-shortener)

### Keyboard Shortcuts
When on a repository page, keyboard shortcuts allow you to navigate easily.

 - Pressing `t` will bring up a file explorer.
 - Pressing `w` will bring up the branch selector.
 - Pressing `s` will select the Command Bar.
 - Pressing `l` will edit labels on existing Issues.
 - Pressing `y` **when looking at a file** (e.g. `https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.md`) will change your URL to one which, in effect, freezes the page you are looking at. If this code changes, you will still be able to see what you saw at that current time.

To see all of the shortcuts for the current page press `?`:

![Keyboard shortcuts](http://i.imgur.com/y5ZfNEm.png)

[*En savoir plus about using the Command Bar.*](https://help.github.com/articles/using-the-commande-bar)

### Line Highlighting in Repositories
Either adding `#L52` to the end of a code file URL or simply clicking the line number will highlight that line number.

It also works with ranges, e.g. `#L53-L60`, to select ranges, hold `shift` and click two lines:

```
https://github.com/rails/rails/blob/master/activemodel/lib/active_model.rb#L53-L60
```

![Line Highlighting](http://i.imgur.com/8AhjrCz.png)

### Closing Issues via Commit Messages
If a particular commit fixes an issue, any of the keywords `fix/fixes/fixed`, `close/closes/closed` or `resolve/resolves/resolved`, followed by the issue number, will close the issue once it is committed to the master branch.

```bash
$ git commit -m "Fix screwup, fixes #12"
```

This closes the issue and references the closing commit.

![Closing Repo](http://i.imgur.com/Uh1gZdx.png)

[*En savoir plus about closing Issues via commit messages.*](https://help.github.com/articles/closing-issues-via-commit-messages)

### Cross-Link Issues
If you want to link to another issue in the same repository, simple type hash `#` then the issue number, it will be auto-linked.

To link to an issue in another repository, `user_name/repo_name#ISSUE_NUMBER` e.g. `tiimgreen/toc#12`.

![Cross-Link Issues](https://camo.githubusercontent.com/447e39ab8d96b553cadc8d31799100190df230a8/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f626c6f672f323031312f736563726574732f7265666572656e6365732e706e67)

### CI Status on Pull Requests
If set up correctly, every time you receive a Pull Request, [Travis CI](https://travis-ci.org/) will build that Pull Request just like it would every time you make a new commit. En savoir plus about how to [get started with Travis CI](http://docs.travis-ci.com/user/getting-started/).

[![Travis CI status](https://cloud.githubusercontent.com/assets/1687642/2700187/3a88838c-c410-11e3-9a46-e65e2a0458cd.png)](https://github.com/octokit/octokit.rb/pull/452)

[*En savoir plus about the commit status API.*](https://github.com/blog/1227-commit-status-api)

### Syntax Highlighting in Markdown Files
For example, to syntax highlight Ruby code in your Markdown files write:

    ```ruby
    require 'tabbit'
    table = Tabbit.new('Name', 'Email')
    table.add_row('Tim Green', 'tiimgreen@gmail.com')
    puts table.to_s
    ```

This will produce:

```ruby
require 'tabbit'
table = Tabbit.new('Name', 'Email')
table.add_row('Tim Green', 'tiimgreen@gmail.com')
puts table.to_s
```

GitHub uses [Linguist](https://github.com/github/linguist) to perform language detection and syntax highlighting. You can find out which keywords are valid by perusing the [languages YAML file](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml).

[*En savoir plus about GitHub Flavored Markdown.*](https://help.github.com/articles/github-flavored-markdown)

### Emojis
Emojis can added to on Pull Requests, Issues, commit messages, Markdown files, etc. using `:name_of_emoji:`:

```
:smile:
```

Would produce:

:smile:

The full list of supported Emojis on GitHub can be found at [emoji-cheat-sheet.com](http://www.emoji-cheat-sheet.com/) or [scotch-io/All-Github-Emoji-Icons](https://github.com/scotch-io/All-Github-Emoji-Icons).

The top 5 used Ejmojis on GitHub are:

1. :shipit: - `:shipit:`
2. :sparkles: - `:sparkles:`
3. :-1: - `:-1:`
4. :+1: - `:+1:`
5. :clap: - `:clap:`

### Images/GIFs
Images and GIFs can be added to comments, READMEs etc.:

```
![Alt Text](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)
```

![Peter don't care](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)

All images are cached on GitHub, so if your host goes down, the image will remain available.

#### Embedding Images in GitHub Wiki
There are multiple ways of embedding images in Wiki pages. There's the standard Markdown syntax (shown above). But there's also a syntax that allows things like specifying the height or width of the image:

```markdown
[[ http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif | height = 100px ]]
```

Which produces:

![Just a screenshot](http://i.imgur.com/J5bMf7S.png)

### Quick Quoting
When on a comment thread and you want to quote something someone previously said, highlight the text and press `r`, this will copy it into your text box in the block-quote format.

![Quick Quote](https://f.cloud.github.com/assets/296432/124483/b0fa6204-6ef0-11e2-83c3-256c37fa7abc.gif)

[*En savoir plus about quick quoting.*](https://github.com/blog/1399-quick-quotes)

### Quick Licensing
When creating a repository GitHub gives you the options of adding in a pre-made license:

![License](http://i.imgur.com/Chqj4Fg.png)

You can also add them to existing repositories by creating a new file through the web interface. When the name `LICENSE` is typed in you will get an option to use a template:

![License](http://i.imgur.com/fTjQict.png)

Also works for `.gitignore`.

[*En savoir plus about open source licensing.*](https://help.github.com/articles/open-source-licensing)

### Task Lists
In Issues and Pull requests check boxes can be added with the following syntax (notice the space):

```
- [ ] Be awesome
- [ ] Prepare dinner
  - [ ] Research recipe
  - [ ] Buy ingredients
  - [ ] Cook recipe
- [ ] Sleep
```

![Task List](http://i.imgur.com/jJBXhsY.png)

When they are clicked, they will be updated in the pure Markdown:

```
- [x] Be awesome
- [ ] Prepare dinner
  - [x] Research recipe
  - [x] Buy ingredients
  - [ ] Cook recipe
- [ ] Sleep
```

[*En savoir plus about task lists.*](https://help.github.com/articles/writing-on-github#task-lists)

#### Task Lists in Markdown Documents
In full Markdown documents **read-only** checklists can now be added using the following syntax:

```
- [ ] Mercury
- [x] Venus
- [x] Earth
  - [x] Moon
- [x] Mars
  - [ ] Deimos
  - [ ] Phobos
```

- [ ] Mercury
- [x] Venus
- [x] Earth
  - [x] Moon
- [x] Mars
  - [ ] Deimos
  - [ ] Phobos

[*En savoir plus about task lists in markdown documents.*](https://github.com/blog/1825-task-lists-in-all-markdown-documents)

### Relative Links
Relative links are recommended in your Markdown files when linking to internal content.

```markdown
[Link to a header](#awesome-section)
[Link to a file](docs/readme)
```

Absolute links have to be updated whenever the URL changes (e.g. repository renamed, username changed, project forked). Using relative links makes your documentation easily stand on its own.

[*En savoir plus about relative links.*](https://help.github.com/articles/relative-links-in-readmes)

### Métadonnées et support des plugins pour GitHub Pages
Within Jekyll pages and posts, repository information is available within the `site.github` namespace, and can be displayed, for example, using `{{ site.github.project_title }}`.

The Jemoji and jekyll-mentions plugins enable [emoji](#emojis) and [@mentions](https://github.com/blog/821) in your Jekyll posts and pages to work just like you'd expect when interacting with a repository on GitHub.com.

[*En savoir plus about repository metadata and plugin support for GitHub Pages.*](https://github.com/blog/1797-repository-metadata-and-plugin-support-for-github-pages)

### Présentation des métadonnées YAML dans vos documents
De nombreux systèmes de blog, tels que [Jekyll](http://jekyllrb.com/) avec [GitHub Pages](http://pages.github.com/), s'appuient sur certaines métadonnées au format YAML au début de votre billet. GitHub affiche ces métadonnées dans un tableau horizontal, pour une meilleure lisibilité.

![Métadonnées YAML](https://camo.githubusercontent.com/47245aa16728e242f74a9a324ce0d24c0b916075/68747470733a2f2f662e636c6f75642e6769746875622e636f6d2f6173736574732f36343035302f313232383236372f65303439643063362d323761302d313165332d396464382d6131636432323539393334342e706e67)

[*En savoir plus sur la présentation des métadonnées YAML dans vos documents.*](https://github.com/blog/1647-viewing-yaml-metadata-in-your-documents)

### Rendu des données tabulaires
GitHub supporte le rendu de données tabulaires sous forme de fichiers `.csv` (comma-separated) et `.tsv` (tab-separated).

![Données tabulaires](https://camo.githubusercontent.com/1b6dd0157ffb45d9939abf14233a0cb13b3b4dfe/68747470733a2f2f662e636c6f75642e6769746875622e636f6d2f6173736574732f3238323735392f3937363436322f33323038336463652d303638642d313165332d393262322d3566323863313061353035392e706e67)

[*En savoir plus le rendu des données tabulaires.*](https://github.com/blog/1601-see-your-csvs)

### Diffs
#### Rendu des diffs de prose    $FIXME$ Improve?
Les commits et pull requests incluant des "documents avec rendu visuel" supportés par GitHub (ex. Markdown) disposent des vues *source* et *rendered*.

![Vue Source / Rendered](https://github-images.s3.amazonaws.com/help/repository/rendered_prose_diff.png)

Cliquez sur le bouton "rendered" pour voir les changements tels qu'ils apparaitront dans le document avec son rendu visuel. La vue Rendered est utile lorsque vous ajoutez, supprimez ou modifiez du texte :

![Rendu des diffs de prose](https://f.cloud.github.com/assets/17715/2003056/3997edb4-862b-11e3-90be-5e9586edecd7.png)

[*En savoir plus sur le rendu des diffs de prose.*](https://github.com/blog/1784-rendered-prose-diffs)

#### Diff pour les Maps
Chaque fois que vous visualisez sur GitHub un commit ou un pull request incluant des données cartographiques, GitHub affiche une représentation visuelle de ce qui a changé.

[![Diff pour les Maps](https://f.cloud.github.com/assets/282759/2090660/63f2e45a-8e97-11e3-9d8b-d4c8078b004e.gif)](https://github.com/benbalter/congressional-districts/commit/2233c76ca5bb059582d796f053775d8859198ec5)

[*En savoir plus sur le diff pour les Maps.*](https://github.com/blog/1772-diffable-more-customizable-maps)

#### Etendre le contexte dans les diffs    $FIXME$
Using the *unfold* button in the gutter of a diff, you can reveal additional lines of context with a click. You can keep clicking *unfold* until you've revealed the whole file, and the feature is available anywhere GitHub renders diffs.

![Expanding Context in Diffs](https://f.cloud.github.com/assets/22635/1610539/863c1f64-5584-11e3-82bf-151b406a272f.gif)

[*En savoir plus about expanding context in diffs.*](https://github.com/blog/1705-expanding-context-in-diffs)

#### Diff ou patch de Pull Request
Vous pouvez obtenir le diff d'un Pull Request en ajoutant l'extension `.diff` ou `.patch` à la fin de l'URL. Par exemple :

```
https://github.com/tiimgreen/github-cheat-sheet/pull/15
https://github.com/tiimgreen/github-cheat-sheet/pull/15.diff
https://github.com/tiimgreen/github-cheat-sheet/pull/15.patch
```

L'extension `.diff` vous donne ceci en texte plein :

```
diff --git a/README.md b/README.md
index 88fcf69..8614873 100644
--- a/README.md
+++ b/README.md
@@ -28,6 +28,7 @@ All the hidden and not hidden features of Git and GitHub. This cheat sheet was i
 - [Merged Branches](#merged-branches)
 - [Quick Licensing](#quick-licensing)
 - [TODO Lists](#todo-lists)
+- [Relative Links](#relative-links)
 - [.gitconfig Recommendations](#gitconfig-recommendations)
     - [Aliases](#aliases)
     - [Auto-correct](#auto-correct)
@@ -381,6 +382,19 @@ When they are clicked, they will be updated in the pure Markdown:
 - [ ] Sleep

(...)
```

#### Rendu et diffing des images
GitHub peut afficher plusieurs formats d'image communément rencontrés, dont le PNG, le JPG, le GIF, et le PSD. De plus, il y a plusieurs façons de comparer les differences entre les versions ce ces formats d'image.

[![Diffable PSD](https://cloud.githubusercontent.com/assets/2546/3165594/55f2798a-eb56-11e3-92e7-b79ad791a697.gif)](https://github.com/blog/1845-psd-viewing-diffing)

[*En savoir plus sur le rendu et le diffing des images.*](https://help.github.com/articles/rendering-and-diffing-images)

### Hub
[Hub](https://github.com/github/hub) est outil en ligne de commande, wrapper autour de Git, qui vous apporte des fonctionnalités et commandes supplémentaires pour faciliter l'utilisation de GitHub.

Cela permet de faire des choses telles que :

```bash
$ hub clone tiimgreen/toc
```

[*Découvrer d'autres commandes intéressantes offertes par Hub.*](https://github.com/github/hub#commandes)

### Réduction de la friction entre contributeurs
Si vous voulez que les gens utilisent votre projet et y contribuent, vous devez commencer par répondre à leurs questions les plus simples. Que fait le projet ? Comment l'utilise-t-on ? Comment suis-je autorisé à l'utiliser ? Comment contribue-t-on ? Comment démarre-t-on pour développer ? Comment puis-je m'assurer que mes nouvelles fonctionnalités n'ont pas introduit de régression sur d'anciennes fonctionnalités ?

[Friction](https://github.com/rafalchmiel/friction) est un script en ligne de commande qui vérifie votre projet par rapport aux [réponses classiques à ces questions](https://github.com/rafalchmiel/friction/wiki). Voici un exemple de résultat :

[![Résultat d'exécution de Friction](http://i.imgur.com/4EgpWo4.png)](https://github.com/rafalchmiel/friction)

*Friction supporte MRI 2.1.0, MRI 2.0.0, et MRI 1.9.3.*

### Guidelines pour contribuer
Si vous ajoutez un fichier `CONTRIBUTING` à la racine de votre dépôt, un lien vers celui-ci est ajouté à chaque nouvelle contribution de type Issue ou Pull Request.

![Contributing Guidelines](https://camo.githubusercontent.com/71995d6b0e620a9ef1ded00a04498241c69dd1bf/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f736b697463682f6973737565732d32303132303931332d3136323533392e6a7067)

[*En savoir plus sur les guidelines pour contribuer.*](https://github.com/blog/1184-contributing-guidelines)

### Ressources GitHub
| Titre | Lien |
| ----- | ---- |
| GitHub Explore | https://github.com/explore |
| GitHub Blog | https://github.com/blog |
| GitHub Help | https://help.github.com/ |
| GitHub Training | http://training.github.com/ |
| GitHub Developer | https://developer.github.com/ |

#### Talks GitHub
| Titre | Lien |
| ----- | ---- |
| How GitHub Uses GitHub to Build GitHub | https://www.youtube.com/watch?v=qyz3jkOBbQY |
| Introduction to Git with Scott Chacon of GitHub | https://www.youtube.com/watch?v=ZDR433b0HJY |
| How GitHub No Longer Works | https://www.youtube.com/watch?v=gXD1ITW7iZI |
| Git and GitHub Secrets | https://www.youtube.com/watch?v=Foz9yvMkvlA |
| More Git and GitHub Secrets | https://www.youtube.com/watch?v=p50xsL-iVgU |

## Git
### Branche précédente
Pour passer de la branche courante à la branche précédente dans Git :

```bash
$ git checkout -
# Passage à la branche 'master'

$ git checkout -
# Passage à la branche 'next'

$ git checkout -
# Passage à la branche 'master'
```

[*En savoir plus sur le Git branching.*](http://git-scm.com/book/en/Git-Branching-Basic-Branching-and-Merging)

### Stripspace

Git Stripspace:

- Enlève les espaces de fin de ligne (FIXME trailing)
- Collapses newlines (FIXME)
- Insère une nouvelle ligne en fin de fichier

Un fichier doit être passé en argument à l'appel de la commande, par ex. :
```bash
$ git stripspace < README.md
```

[*En savoir plus sur la commande Git `stripspace`.*](http://git-scm.com/docs/git-stripspace)

### Récupérer des Pull Requests

Les Pull Requests sont des branches spéciales sur le dépôt GitHub qui peuvent être récupérées localement de plusieurs manières :

Récupérer un Pull Request spécifique et le stocker temporairement dans le `FETCH_HEAD` pour faire rapidement un `diff` ou un `merge` :

```bash
$ git fetch origin refs/pull/[PR-Number]/head
```

Récupérer toutes les branches de Pull Request en tant que branches distantes (remote) locales par refspec :

```bash
$ git fetch origin '+refs/pull/*/head:refs/remotes/origin/pr/*'
```

Ou paramétrer le remote pour récupérer les Pull Requests automatiquement en ajoutant dans le fichier `.git/config` de votre dépôt des lignes telles que :

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
```

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
    fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```

Pour les contributions de Pull Requests basés sur un fork, cela aide de faire un `checkout` d'une branche remote représentant le Pull Request et de créer une branche locale à partir de celle-ci :

```bash
$ git checkout pr/42 pr-42
```

[*En savoir plus sur la récupération de Pull Requests en local.*](https://help.github.com/articles/checking-out-pull-requests-locally)

### Commits vides :trollface:
Il est possible de faire des commits de code sans aucun changement en ajoutant `--allow-empty` :

```bash
$ git commit -m "Big-ass commit" --allow-empty
```

Voici des cas d'utilisation (qui ont du sens) pour ça :

 - Annoter le début d'un nouveau lot de changements ou d'une nouvelle fonctionnalité.
 - Documenter les changements non relatifs à du code que vous faites pour le project.
 - Communiquer avec les gens en utilisant le dépôt.
 - Le premier commit d'un dépôt, vu que le premier commit ne peut pas être rebasé par la suite : `git commit -m "init repo" --allow-empty`.

### Personnaliser le format du status Git
Exécuter :

```bash
$ git status
```

Produit :

![git status](http://i.imgur.com/o3PEHAA.png)

En ajoutant `-sb`:

```bash
$ git status -sb
```

Cela produit :

![git status -sb](http://i.imgur.com/xNI1bT0.png)

[*En savoir plus sur la commande Git `status`.*](http://git-scm.com/docs/git-status)

### Personnaliser le format du log Git
Exécuter :

```bash
$ git log --all --graph --pretty=format:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

Produit :

![git log --all --graph --pretty=format:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative](http://i.imgur.com/EARRQyJ.png)

Crédit à [Palesz](http://stackoverflow.com/users/88355/palesz)

*Il est possible de créer un alias pour ça en suivant les instructions [ici](https://github.com/tiimgreen/github-cheat-sheet#aliases).*

[*En savoir plus sur la commande Git `log`.*](http://git-scm.com/docs/git-log)

### Requête Git
Une requête Git permet de chercher dans tous vos précédents messages de commit et trouver le plus récente correspondant à la requête.

```bash
$ git show :/query
```

Où `query` (respecter la casse) est le terme que vous voulez chercher. Trouve la dernière occurence et donne des détails sur les lignes qui ont été changées.

```bash
$ git show :/typo
```
![git show :/query](http://i.imgur.com/icaGiNt.png)

*Entrez `q` pour quitter.*

### Branches fusionnées
Exécuter:

```bash
$ git branch --merged
```

Donne la liste de toutes les branches qui ont été fusionnées dans votre branche courante.

A l'inverse:

```bash
$ git branch --no-merged
```

Donne la liste des branches qui n'ont pas été fusionnées dans votre branche courante.

[*En savoir plus sur la commande Git `branch`.*](http://git-scm.com/docs/git-branch)

### Serveur web pour naviguer dans les dépôts locaux
Utilisez la commande Git `instaweb` pour naviguer, de manière instantanée, au sein de votre répertoire de travail dans `gitweb`. Cette commmande exécute un script pour configurer `gitweb` et un serveur web pour naviguer dans le dépôt local.  

```bash
$ git instaweb
```

Ouvre:

![Git instaweb](http://i.imgur.com/Dxekmqc.png)

[*En savoir plus sur la commande Git `instaweb`.*](http://git-scm.com/docs/git-instaweb)

### Configurations Git
Votre fichier `.gitconfig` contient tous vos éléments de configuration de Git.

#### Les alias
Les alias vous aident à définir vos propres appels git. Par exemple, vous pourriez définir `git a` pour exécuter `git add --all`.

Pour ajouter un alias, éditez `~/.gitconfig` et mettez-y la définition en respectant le format suivant :

```
[alias]
  co = checkout
  cm = commit
  p = push
  # Show verbose output about tags, branches or remotes
  tags = tag -l
  branches = branch -a
  remotes = remote -v
```

... ou entrez en ligne de commande :

```bash
$ git config --global alias.new_alias fonction_git
```

Par exemple :

```bash
$ git config --global alias.cm commit
```

S'il s'agit d'un alias pour plusieurs fonctions, utilisez les quotes :

```bash
$ git config --global alias.ac 'add -A . && commit'
```

Voici quelques alias utiles :

| Alias | Commande | Ce qu'il faut entrer |
| --- | --- | --- |
| `git cm` | `git commit` | `git config --global alias.cm commit` |
| `git co` | `git checkout` | `git config --global alias.co checkout` |
| `git ac` | `git add . -A` `git commit` | `git config --global alias.ac '!git add -A && git commit'` |
| `git st` | `git status -sb` | `git config --global alias.st 'status -sb'` |
| `git tags` | `git tag -l` | `git config --global alias.tags 'tag -l'` |
| `git branches` | `git branch -a` | `git config --global alias.branches 'branch -a'` |
| `git remotes` | `git remote -v` | `git config --global alias.remotes 'remote -v'` |
| `git lg` | `git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --` | `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"` |

*Certains de ces alias proviennent des dotfiles de [@mathiasbynens](https://github.com/mathiasbynens) : https://github.com/mathiasbynens/dotfiles/blob/master/.gitconfig*

#### Auto-correction
Si vous entrez `git comit` vous aurez ceci :

```bash
$ git comit -m "Message"
# git: 'comit' is not a git commande. See 'git --help'.

# Did you mean this ?
#   commit
```

Pour exécuter `commit` lorsque `comit` est entré, activez simplement l'auto-correction :

```bash
$ git config --global help.autocorrect 1
```

Ainsi, maintenant, vous aurez ceci :

```bash
$ git comit -m "Message"
# WARNING: You called a Git commande named 'comit', which does not exist.
# Continuing under the assumption that you meant 'commit'
# in 0.1 seconds automatically...
```

#### Couleur
Ajouter plus de couleurs à votre sortie Git :

```bash
$ git config --global color.ui 1
```

[*En savoir plus sur la commande Git `config`.*](http://git-scm.com/docs/git-config)

### Ressources Git
| Titre | Lien |
| ----- | ---- |
| Official Git Site | http://git-scm.com/ |
| Official Git Video Tutorials | http://git-scm.com/videos |
| Code School Try Git | http://try.github.com/ |
| Introductory Reference & Tutorial for Git | http://gitref.org/ |
| Official Git Tutorial | http://git-scm.com/docs/gittutorial |
| Everyday Git | http://git-scm.com/docs/everyday |
| Git Immersion | http://gitimmersion.com/ |
| Ry's Git Tutorial | http://rypress.com/tutorials/git/index.html |
| Git for Designer | http://hoth.entp.com/output/git_for_designers.html |
| Git for Computer Scientists | http://eagain.net/articles/git-for-computer-scientists/ |
| Git Magic | http://www-cs-students.stanford.edu/~blynn/gitmagic/ |
| GitHub Training Kit | http://training.github.com/kit |

#### Livres Git
| Titre | Lien |
| ----- | ---- |
| Pragmatic Version Control Using Git | http://www.pragprog.com/titles/tsgit/pragmatic-version-control-using-git |
| Pro Git | http://git-scm.com/book |
| Git Internals Peepcode | http://peepcode.com/products/git-internals-pdf |
| Git in the Trenches | http://cbx33.github.com/gitt/ |
| Version Control with Git | http://www.amazon.com/Version-Control-Git-collaborative-development/dp/1449316387 |
| Pragmatic Guide to Git | http://www.pragprog.com/titles/pg_git/pragmatic-guide-to-git |
| Git: Version Control for Everyone | http://www.packtpub.com/git-version-control-for-everyone/book |
