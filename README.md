# DEMYSTIFYING-MMD-GANS
The goal of the project is to  implement and analyse the performance , limits of a method of improving the stability of the GAN's training:  Using an MMD as a critic.
# Remarks from meeting sessions
**Meeting 1**

the goal of training MMD GANS is to minimise the loss MMD, 
For implementation :



1. Start with applying an (exiplicit) kernel direct : we can start with small datasets in 2d. And test the same algorithm on bigger directly.


2. Move to a learned kernel with the form k(h(.),h(.)). Either use a fixed kernel or a train h.




3.Highlight stability of the learning of the kernel, Evaluate convergence.


**Meeting 2**:


1.Highlight the effect of tuning parameters on the MMD Learning : effect on the descriminator decision boundary, learning stability.



# Timeline
**10/05/2026**: (Mohamed) Lecture du papier principal "Demystifying MMD GANs" (sauf la section "Gradient bias") .
**11/05/2026**: (Nous tous) Réunion1 avec le prof.


**17/05/2026**: Relecture du papier , Compléter le TP Lab1 dédiée à l'entrainement de GAN , WGAN sur des données 2D synthétiques.

**19/05/2026**: Implémentation de l'entrainement des MMD GAN sur les données 2D synthétiques.


**20/05/2026**: Réunion 2 avec le prof.

**25/05/2026**: Correction de la partie du code du descriminateur dans l'entrainement du MMd, Expérimentation de l'entrainement en utilisant le noyau rbf/quadraatic rational kernel  sur des données syntthétiques 2d en utilisant différenttes valeurs de $\sigma / \alpha$ , rédaction de quelques remarques liés au choix de sigma , l'infuluence dee la nature de la distribution sur l'entrainement du réseau génératif.

**30/05/2026** Une déscription théorique de l'effet de la bande passante du noyau choisie , de la nature de la distribution originale sur l'apprentissage u générateur. Cette déscription étaitinspirée des résultats des expériences sur les données synthétiques 2d  .Le théorème de Bernier autour du transport optimal a permis d'éclaircir la remarque à propos de la tendance du réseau à apprendre une distribution de support  "plus convexe" que la distribution originale qui est une simple somme de diracles.


**31/05/2026** Tentative d'entrainement d'un MMD GAN sur la base d'images CIFAR (170 M , grande variabilité sémantique comparée à MNIST par exemple) . Pour le moment , je n'ai pas réussit à générer des images plausibles sémantiquement (images générées plus proche de bruit que d'images réelles)


# Macro-Planning
**Week 3**
Correcting errors mentioned in the previous meeting 

Analysis of the role of hyperparameters, choice of the kernel used.


 If we succeed to achieve stability on toy examples , MNIST , CIFAR , We move to larger datasets (More natural images)

**Week 4**
Quantitative analysis of performance , limits of the metrics used.

**Week 5**

**Week 6**


