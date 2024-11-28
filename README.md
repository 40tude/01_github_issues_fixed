# Intro
Je veux tester au moins 2 cas qui me mettent toujours en panique

# Gros Fichier - Cas 1
J'ai un projet qui est synchronisé sur GitHub  
J'ajoute un fichier > 100 MB  
J'oublie d'en tenir compte dans .gitignore  
Je commit  
Je synchronize  

## PANIQUE!

<p align="center">
<img src="./assets/img01.png" alt="drawing" width="600"/>
<p>


<p align="center">
<img src="./assets/img02.png" alt="drawing" width="600"/>
<p>

Il semble qu'il a rien poussé    
J'édite ``.gitignore``  
Je prends 2 captures d'écran que je met dans un dosier ``./assets``
Je pouse et je synchronise

Même problème


``git reset --soft HEAD~2``

Ca nous ramène à 2 commits en arrière

`git rm --cached .\data\large_file.csv`

Le gros fichier n'est plus suivi


<p align="center">
<img src="./assets/img03.png" alt="drawing" width="600"/>
<p>

Editer ``.gitignore``  


```git
# -----------------------------------------------------------------------------
# files to ignore
secrets.ps1
.env
Jenkinsfile
*.log

# too big
large_file.csv

# -----------------------------------------------------------------------------
# directories to ignore
.git/
.vscode/

# "**/.mypy_cache/" ignore all directories named ".mypy_cache/""
**/.mypy_cache/
**/__pycache__/
**/mlruns/ 
**/logs/
```

Tout sauver  
Fair un ``commit``  
Faire un   

``git push origin main --force``  

* **SYNCHRONIZE** (pull + push) n'est **PAS** suffisant ici 
* car les historiques local et distants ne sont plus synchros

### **Différence entre Synchronize et git push --force**
| **Action**         | **Synchronize**                              | **git push --force**                     |
|---------------------|---------------------------------------------|------------------------------------------|
| **Récupération des modifications distantes** | Fait un `pull` avant le `push`.         | Ne fait aucun `pull`.                    |
| **Gestion des désalignements**    | Échoue si l’historique diverge.         | Écrase l’historique distant.             |
| **Cas d’utilisation** | Cas normaux (pas de désalignement).         | Réécriture d’historique ou conflits majeurs. |

## PLUS de PANIQUE...




# Gros Fichier - Cas 2
J'ai un projet qui est synchronisé sur GitHub  
J'ajoute un fichier > 100 MB  
J'oublie d'en tenir compte dans .gitignore  
Je commit  

Je réalise que j'ai un gros fichier...

## PANIQUE!

