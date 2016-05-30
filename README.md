# TP NoSQL
Réponses aux questions du TP NO SQL

##Partie 1
**1) Vérifiez qu'aucun processus mongo tourne actuellement sur votre machine. Si c’est
le cas, arretez­le. Ensuite lancez une instance mongod avec le dbpath par défaut.
Connectez­vous sur le shell mongo et affichez le port utilisé et less infos du host
depuis le shell.**

```
mongod
```

**2) Arretez le processus depuis le shell.**

```
mongod --shutdown
```

**3) Lancez à nouveau une instance de mongod mais cette fois, modifiez le dbpath et le
fichier de sortie de logs. Connectez vous sur le shell et affichez les infos utilisées
pour la configuration du processus. Vérifiez aussi que les logs sont bien écrit dans le
fichier avec un tail ­f​ou un cat.​**

```
mongod --logpath /data/log/mongodb.log --dbpath /data/testpath
```

**4) Faites l’import des données contenues dans le fichier zip donnée par l’enseignant
afin de construire une base de données appelé “music”​**

```
mongoimport --db dbname --collection music --drop --file mymusic/songs.metadata.json
```

##Partie 2

**1) Affichez les documents de la collection songs.**

**2) Comptez le nombre de documents existants dans la collection songs.**

**3) Affichez exclusivement les titres des chansons du Coldplay de l’album X&Y**

**4) Affichez le titre et album des chansons de Stromae, ordonnés par année de la plus
récente à la plus ancienne, et triés par ordre alphabétique par titre**

**5) Affichez les chansons du group Coldplay dans un tableau, où les éléments sont des
strings ayant comme format TITRE (ALBUM). La sortie doit être comme ça : (voir PDF)**

**6) Affichez, une seule fois, le noms des artistes ayant produit des chansons entre 2002
et 2005**

**7) Créez une collection recordLabel, qui puisse stocker maximum 3 documents ou 1 KB
et dont la structure doit être : (voir PDF)**
