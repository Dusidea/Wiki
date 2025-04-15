# Github common issues
## démarrage manuel de l'agent SSH:

```
eval "$(ssh-agent -s)"
```


## Ajouter chaque clé SSH à ton agent SSH

```
ssh-add ~/.ssh/id_rsa_github_main       (pour moi gmail)
ssh-add ~/.ssh/id_rsa_github_second     (pour moi TestLplanes)
```

## Cloner un repo et le pousser vers un nouveau repo (travailler sur une copie)

Dans le repertoire local :
- git init
- git clone [URL du repo à copier]
- git add *
- git commit -m "First commit"
- git branch -M main
- git remote add origin [URL du nouveau repo : la copie de travail]
- git push -u origin main



