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


**31/05/2026** Tentative d'entrainement d'un MMD GAN sur la base d'images CIFAR (170 M , grande variabilité sémantique comparée à MNIST par exemple) . Pour le moment , je n'ai pas réussit à générer des images plausibles sémantiquement (images générées plus proche de bruit que d'images réelles).
Architecture:
Générateur (transforme un bruit blanc de dimension $n_z$ vers une image à 3 canaux) constituée de convolution transposée ($z_n$ inférieure à la dimension des images)

Calcul de MMD dans un espace latent( dimension $d$) en utilisant un encodeur (initialisé avec les poids de resnet mais qui se met à jour lors de l'entrainement pour maximiser MMD dans l'espace latent entre les images réelles et celles générées par le générateur.

Le choix de $n_z$ (dimension du bruit blanc de départ) semble etre lié à la variabilité de la distribution qu'on vent apprendre."L'énergie du bruit blanc" doit etre de plus en plus grande pour apprendre une distribution de plus en plus variable. 
Les autres choix des learning rates , dimension de l'espace latent étaient choisis en essayant quelques valeurs (sans garantis théoriques mais en s'inspirant des implémentations décrites dans les papiers existants)


**28/05/2026** — Mahdi
- Diagnosed the post-17k training degradation.
- Identified that disabling the activation regularization term (`λ_act = 0`) left critic features unbounded, causing kernel saturation.

**29/05/2026** — Mahdi
- Introduced a scale-targeted activation penalty (`τ = 1`).
- Added a one-sided gradient penalty.
- Implemented learning-rate decay.
- Added best-model checkpointing based on KID score.

**30/05/2026** — Mahdi
- Evaluated the previous modifications.
- Observed that the fix was unsuccessful:
  - KID remained stuck at approximately `3.0`.
  - Generated samples collapsed to nearly black images.

**31/05/2026** — Mahdi
- Replaced the critic with an autoencoder-based critic.
- Added reconstruction loss (`λ_AE = 8`).
- Replaced previous regularization penalties with spectral normalization.
- Optimized the unbiased MMD objective (`MMD²_u`).
- Set the critic update ratio to `n_critic = 5`.


**31/05/2026**
[Training an MMD GAN on CIFAR10 ]: Using a "frozen" Resnet network in the critic : Some textures are generated , but the learning process converges early to a sub-optimal solution: The generator succeeded to minimize MMD , but the MMD itself (computed on the fixed features)  wasn't meaningfull.


**01/06/2026** — Mahdi
- Replaced the fixed kernel bandwidth with the median-distance heuristic.
- Set the base bandwidth as `σ₀² = median(||x − y||²)`.
- Applied the heuristic to the kernel function `k(x, y) = f(||x − y||²)`.

**01/06/2026** 
Updating the bandwith analysis with a quantitative result in the case of a kernel of the form $k(x,y)= f(||x-y||^2)$.
Adding an example of current generator's images trained on CIFAR.

**02/06/2026**
We held a meeting to coordinate and align on what each member of the group has accomplished so far.

**03/06/2026**
Using the same strategy used on Mnist : using an autoencoder with an autoencoder loss. I used  256 dimension for the latent space where i computed the MMD . The learning process was blocked in an early non-optimal phase.
# Macro-Planning
**Week 3**
Correcting errors mentioned in the previous meeting 

Analysis of the role of hyperparameters, choice of the kernel used.


 If we succeed to achieve stability on toy examples , MNIST , CIFAR , We move to larger datasets (More natural images)

**Week 4**
Quantitative analysis of performance , limits of the metrics used.

**Week 5**

**Week 6**


