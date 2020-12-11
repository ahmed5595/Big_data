# Big_data
## Au debut on import pyspark
```
import pyspark
```
## aprés on crée un spark context sur le directory local
```
sc = pyspark.SparkContext('local[*]')
```
## on import le fichier text 
```
txt = sc.textFile('text.txt')
```

## On crée une varible word permettant de mettre le contenu du fichier sous forme d'un vecteur ou chaque ligne contient un seul mot
```
words=txt.flatMap(lambda line: line.split(" "))
```
## On crée une nouvelle variable wordCounts qui contient pour chaque mot le nombre d'occurence pour ce faire  on affecte pour chaque mot un clé de 1 puis on fait la somme
```
wordCounts = words.map(lambda word: (word, 1)).reduceByKey(lambda a,b:a +b)
```
## On export le resultat obtenu dans un fichier text
```
wordCounts.saveAsTextFile("Result")
```
