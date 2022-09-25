# Print extension

[Version français](https://github.com/PeterWone/vsc-print) par Peter Wone

[ENGLISH](README.md) | [FRANCAISE](README.fra.md) | [DEUTSCH](README.deu.md) | [ESPAGNOLE](README.esp.md) | [中文CHINESE](README.zho.md) | [Add a language](how-to-add-a-language.md)

## Impression

### Configuration pour imprimer sur un hôte distant

Vous devez installer l’extension Print sur le système cible. Si l’hôte cible est votre poste de travail, aucune autre action n’est requise, mais lorsque l’hôte cible est un hôte distant, vous devez également installer l’extension Print sur l’hôte distant. 

1. Connectez-vous à l’hôte distant
2. Cliquez sur l’icône des extensions dans la bordure gauche de l’interface utilisateur VS Code. 
3. Trouvez l’extension Imprimer. 
4. Il devrait avoir un petit badge sur lui offrant d’installer sur l’hôte distant. Cliquez sur le badge et VS Code le prendra à partir de là.

Vous devez le faire à nouveau pour chaque hôte distant différent auquel vous vous connectez (différents conteneurs Docker, par exemple).

Les extensions Markdown doivent également être installées sur l’hôte cible si vous souhaitez les utiliser.

### Pour imprimer le document actif

Pour imprimer le document actif, cliquez sur l'icône de l'imprimante à droite des onglets du document.

### Pour imprimer une sélection dans le document actif

Sélectionnez au moins une ligne dans le document actif. Ensuite, cliquez sur l'icône de l'imprimante à droite des onglets du document ou cliquez à droite sur la sélection et choisissez `Print` dans le menu contextuel. Lorsque le menu contextuel apparaît, `Print` apparaît en haut (ou près) en haut, en bas ou nulle part en fonction du paramètre `imprimer.positionAuMenuContextuelDeLEditeur`.

Les numéros de ligne de votre impression sont alignés avec les numéros de ligne de l'éditeur, qu'ils soient visibles ou non. Donc, si vous discutez d'une ligne de code numérotée 1145 dans un réexamen de code et que vous ouvrez le fichier pour l'amender, en tapant `Ctrl+G` puis 1145 `Enter` mettra votre curseur directement sur la ligne de code en question.

### Pour imprimer un fichier (sans l'ouvrir)

Pour imprimer un fichier autre que le document actif, trouvez-le dans le volet EXPLORER et cliquez à droite dessus. Au menu contextuel du fichier `Imprimer` apparaît toujours en haut du menu ou près de celui-ci. Ceci imprime le fichier entier.

### Pour imprimer tous les fichiers dans un répertoire
Si vous appuyez sur `F1` et tapez `imprimer le répertoire`, vous découvrirez que vous pouvez imprimer tous les fichiers contenus dans le répertoire du document actif. Un seul impression est créé avec tous les fichiers séparés par des titres affichant leurs noms de fichiers.

## Paramètres

Cette extension comporte les paramètres suivants, qui peuvent être modifiés en allant dans le code Préférences > Paramètres > Extensions > Impression:

* `print.alternateBrowser` : activer/désactiver un navigateur alternatif
* `print.announcePortAcquisition` : faites en sorte que le serveur web intégré vous dise quel port il utilise
* `print.browserPath` : le chemin (path) vers un navigateur web
* `print.colourScheme` : la feuille de style utilisée pour colorier la syntaxe
* `print.editorContextMenuItemPosition` : la position de la commande `Imprimer` au menu contextuel de l'éditeur
* `print.editorTitleMenuButton` : afficher le bouton Imprimer dans le menu titre de l’éditeur
* `print.fontSize` : la taille de lettrage (options de 6 à 13 pt)
* `print.formatMarkdown` : rendre le Markdown comme HTML stylé lors de l'impression
* `print.lineNumbers` : on, off ou inherit (faire la même chose que l'éditeur)
* `print.lineSpacing` : simple, ligne et demie ou double espacement
* `print.printAndClose` : après l'impression, fermez le navigateur.
* `print.folder.include` : modèles à inclure lors de l’impression. Vide correspond à tout.
* `print.folder.exclude` : modèles à exclure lors de l’impression.
* `print.folder.maxLines` : les fichiers avec plus de lignes que cela seront ignorés.

### Choix de caractère

Bien que la taille de lettrage soit contrôlée par les paramètres, la _police de caractères_ est déterminée par les paramètres de votre éditeur. Si vous voyez Fira Code à l'écran, c'est ce qui sera imprimé.

## Markdown

Lorsque vous Markdown vous voulez probablement qu'il soit rendu et stylisé, et c'est le comportement par défaut. Si, pour des raisons ineffables, vous souhaitez imprimer le texte brut, vous pouvez dévérifier le paramètre `imprimer.rendreLeMarkdown`.

## Navigateur alternatif

Vous pouvez imprimer avec un navigateur autre que votre navigateur par défaut.

Pourquoi souhaiter le faire ?

* Chromium, Edge Dev et Chrome sont les seuls navigateurs qui se ferment correctement après l'impression. Cela en fait les meilleurs choix pour l'impression, mais vous pouvez avoir une préférence différente pour l'utilisation quotidienne du Web.
* Cela peut être pratique pour le dépannage. Peut-être que vous êtes l'élaboration de votre propre feuille de style et que vous voulez être en mesure d'arrêter le navigateur de fermer après l'impression afin que vous puissiez inspecter à l'écran.
* Une autre raison que je ne peux pas imaginer.

Pour configurer un autre navigateur, vous devez faire deux choses :

1. Fournir le chemin au navigateur exécutable dans le paramètre `Imprimer: Chemin de stockage du navigateur`. Sur Windows, il pourrait être quelque chose comme `C:\Program Files (x86)\Google\Chrome\Application\Chrome.exe`
1. Activer/désactiver le navigateur alternatif à l'aide du paramètre 'Imprimer: Navigateur alternatif'

## Choisissez un schéma de couleurs

Les feuilles de style personnalisées ne sont plus prises en charge. Les feuilles de style disponibles sont regroupées et peuvent être choisies par nom dans une liste. Les choix sont limités aux feuilles de style légères car le papier est blanc.

## Extension de Markdown de Katex
Cela dépend de CSS et polices des caractères du web. Pour que l'impression fonctionne, vous devez ajouter la feuille de style requise à vos paramètres.

		"markdown.styles": [
			"https://cdn.jsdelivr.net/npm/katex@0.15.1/dist/katex.min.css"
		]

Voici quelques échantillons pour vous aider à vérifier votre configuration.

```
$$
\begin{alignedat}{2}
   10&x+ &3&y = 2 \\
   3&x+&13&y = 4
\end{alignedat}
$$
and thus

$$
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
$$
```

# Extensions Markdown et espaces de travail distants

Pour travailler avec des espaces de travail distants, une extension Markdown doit s’exécuter sur l’hôte distant, car c’est là que le pipeline de rendu Markdown s’exécute. La plupart des extensions Markdown fonctionneront comme ça, mais elles ne sont pas configurées pour cela.

Le problème est que la plupart d’entre eux ne sont pas configurés de cette façon, même s’il suffirait d’une entrée dans leur fichier `package.json`. 

Heureusement, vous pouvez les patcher vous-même. 

1. Trouvez les extensions où elles sont installées sur votre poste de travail dans `~/.vscode/extensions` (sous Windows, remplacez `%userprofile%` par `~`)
2. Modifiez les fichiers `package.json` pour les extensions Markdown que vous souhaitez utiliser sur les hôtes distants. Ajoutez l’attribut `extensionKind`. 
3. Lorsque vous avez modifié toutes les extensions Markdown, redémarrez VS Code.

C’est un attribut de niveau racine afin que vous puissiez le mettre dès le début. Si cet attribut est déjà présent, VS Code vous le dira bientôt. Pour fonctionner correctement avec la réunion à l’amiable, il doit spécifier « espace de travail ». Ne mettez pas à la fois `workspace` et `ui`. Si vous faites cela, VS Code préférera la station de travail locale et ne fonctionnera que pour les fichiers locaux. 
Vous devez le déterminer par l’espace de travail. 

Que se passe-t-il si vous disposez d’un espace de travail distant, mais qu’un éditeur contient un fichier local ? Lorsque ce fichier local est du code source, l’impression fonctionne. Pour Markdown qui est exempt de références de ressources, l’impression fonctionnera. Mais les références Markdown aux images seront résolues dans le système de fichiers distant et les images ne seront pas trouvées.

```json
{
  "extensionKind": [
    "workspace"
  ],
  "name": "vscode-print",
  "displayName": "Print",

```
