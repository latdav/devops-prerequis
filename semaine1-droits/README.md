# Semaine 1 : utilisateurs, groupes et droits 

## Objectif 
Creer un dossier partage ou seule l'equipe peut travailler. 


## Mise en place 
```

sudo useradd -m alice 
sudo useradd -m bob 
sudo useradd -m carla 
sudo groupadd equipe 
sudo usermod -aG equipe alice 
sudo usermod -aG equipe bob 
sudo mkdir -p /srv/partage
sudo chgrp equipe /srv/partage 
sudo chmod g+rwx,o-rwx,g+s /srv/partage 
``` 


## Verification 
- `ls -ld /srv/partage`affiche `drwxrws---root equipe`

- alice (membre) peut creer un fichier 

- carla (non membre) recoit `Permission denied`

- grace au droit `s`, les nouveaux fichiers prennent le groupe `equipe`


## Ce que j'ai appris 
- Lire les droits `rwx`par bloc : proprietaire, groupe, autres 
- Linux applique un seul bloc, le premier qui concerne l'utilisateur 
- `root`ignore `r`et `w`, mais exige un `x`pour executer 


