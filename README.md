# Classification-CAH
Projet algorithmique du S2 visant à développer une série de classes Python permettant de mettre en œuvre l'algorithme de classification non supervisé CAH (classification ascendante hiérarchique)

# Classification Ascendante Hiérarchique (CAH)

Ce code Python implémente l'algorithme de Classification Ascendante Hiérarchique (CAH) pour regrouper des textes en fonction de leur similarité.

# Fonctionnalités

* ### Menu de navigation:
L'utilisateur peut choisir via un menu de navigation à choix s'il souhaite ajouter ou supprimer des textes, ou lancer l'algorithme de classification. Si l'utilisateur entre un mauvais choix, un message d'erreur est renvoyé.

* ### Importation de texte:
**def import_text(text_type:in, source:str) -> str**

Le code permet d'importer des textes à partir de différentes sources (url, fichier, chaîne de caractère en entrée).

* ### Filtrage des mots avec une stoplist
**def read_stoplist(filename: str) -> set:**

Permet de filtrer les mots outils lors de l'instanciation d'un objet CAH.

* ### Tokenisation:
**def tokenize(text : str) -> list:**

Les textes sont tokenisés à l'aide d'une expression régulière pour séparer les mots.


* ### Classification ascendante hiérarchique: 

L'algorithme de CAH est utilisé pour regrouper les textes en clusters en fonction de leur similarité.

Classe CAH: 

* #### Ajouter des textes provenant de différentes sources:
    **def add_text(self, text_list: list):**

* #### Supprimer un texte selon le label:
    **def del_text(self, label_to_delete):**

* #### Accéder aux données de data:
    **def get_data(self):**

* #### Classification:
    **def classify(self, n: int, min_sim: float) -> list:**
Il existe deux version avec des codes classify différents, un utilisant les indices et le deuxième deepcopy.

* #### TF-IDF:
    ** def tf_idf(self) -> dict:**
Ce code est uniquement implémenté pour la version 2.


* #### Calcul de similarité:

    **def sim_cosinus(vect1: dict, vect2: dict) -> float:** 

* #### Transformation des textes en vecteur:

    **def text2vec(tokens, stoplist) -> dict:**

* #### Chercher la dissimilarité minimale:
    **def find_min_sim(dissims_list): -> float**

* #### Calculer la dissimilarité entre deux clusters donnés:
    **def _dissim(cluster1: list, cluster2: list) -> float:**

# Utilisation

Importation des modules

Ce script Python utilise plusieurs modules:

    requests : Pour effectuer des requêtes HTTP lors de l'importation de texte à partir d'une URL.

    BeautifulSoup : Pour l'analyse de la structure HTML lors de l'importation de texte à partir d'une URL.

    string : Pour manipuler des chaînes de caractères.

    re : Pour effectuer des opérations de recherche et de remplacement avec des expressions régulières.
    
    math : Pour effectuer des opérations mathématiques.

Importer les données de test.

Lancer l'algorithme.

Pour faire fonctionner le code, il faut absolument spécifier la stoplist. Sur google colab ```/content/stoplist.txt```

Puis choisir l'action à exécuter : 
* 1 : Ajouter un texte
* 2 : Supprimer un texte
* 3: Afficher data
* 4: Exécution de l'algorithme

### 1. Ajouter un texte

L'utilisateur peut ajouter plusieurs textes sous cette forme:
[("label1", "type1", "source1"), ("label2", "type2", "source2"), ...] Suivant le type spécifié (1 pour url, 2 pour fichier et 3 pour chaîne de caractère) le code va traiter différemment l'import de textes avec la fonction import_text().

exemple : 


[("URL", "1", "https://fr.wikisource.org/wiki/Histoires_ou_Contes_du_temps_pass%C3%A9_(1697)/Petit_Chaperon_rouge"), ("Fichier", "2", "/content/texte3.txt"), ("Chaine de caractères", "3", "l estoit une fois un roi et une reine qui estoient si faschez de n’avoir point d’enfans, si faschez qu’on ne sçauroit dire. Ils allerent à toutes les eaux du monde : vœux, pelerinages, menuës devotions, tout fut mis en œuvre, et rien n’y faisoit. Enfin, pourtant, la reine devint grosse, et accoucha d’une fille. On fit un beau baptesme ; on donna pour maraines à la petite princesse toutes les fées qu’on pust trouver dans le pays (il s’en trouva sept), afin que, chacune d’elles luy faisant un don, comme c’estoit la coustume des fées en ce temps-là, la princesse eust, par ce moyen, toutes les perfections imaginables.")]

Vous trouverez les données de tests en bas à l'onglet "Tests et résultats".

### 2. Supprimer un texte

L'uilisateur peut supprimer un texte un par un en entrant le label du texte qu'il veut supprimer.

ex. Fichier

### 3. Afficher data
L'utilisateur peut afficher data qui correspond à une liste de dictionnaire contenant des vecteurs et leur label.

### 4. Lancer l'algorithme

L'utilisateur doit spécifier le nombre de clusters finaux voulus, ainsi que la similarité minimale.
L'algorithme renvoie une liste contenant les labels regroupés.
ex. 
['Chaperon', 'Recette']
['Fichier', 'Chat', 'Barbe', 'Belle']

# Amélioration et bug 

Quelques fonctionnalités auraient pu être ajoutées : 

* Ajout d'une tokénisation différente selon les langues
* Ajout du calcul tf_idf (implanté uniquement dans la version 2 du code)
* Ajout de la modélisation en dendogramme 

# Bugs
Gestion des erreurs : 
* Lorsque le chemin de la stoplist n'est pas bien spécifié, le code s'exécute malgré tout mais plante après.
* Pour la version 2 du code, l'algorithme classify renvoie un nombre de cluster à partir de 3.
