# REAL NVP (Real-valued Non-Volume Preserving)

REAL NVP est un modèle de **flow normalisant** publié en 2017 par **Laurent Dinh et al.**,  
de l'équipe DeepMind chez Google. Il appartient à la famille des **modèles à flux normalisants**,  
où une variable aléatoire complexe est transformée de manière bijective en une distribution  
plus simple, généralement une gaussienne.

Pour l'inférence, un échantillon est d'abord tiré depuis une distribution normale centrée réduite.  
En appliquant les transformations inverses apprises par le modèle, on reconstruit ainsi une donnée réaliste  
dans l'espace original. Ce processus est rapide et ne nécessite pas d'itérations successives  
comme dans les modèles génératifs traditionnels.

L'apprentissage de cette transformation repose sur des **coupling layers**, qui permettent de garantir  
une inversion simple tout en maintenant une grande flexibilité dans la modélisation de la distribution.  
Chaque coupling layer divise les données en deux parties :  
- Une partie laissée inchangée
- Une partie transformée de manière paramétrique en fonction de l'autre

Cette alternance de transformations assure qu’au fil des couches, **toutes les dimensions des données**  
sont progressivement modifiées. De plus, elle permet un calcul efficace du jacobien, évitant ainsi  
le coût exponentiel souvent associé aux modèles de densité explicite.

L'entraînement de REAL NVP repose sur la **maximisation de la vraisemblance**,  
permettant un apprentissage stable sans besoin de techniques adversariales.  
