# DEMYSTIFYING-MMD-GANS
The goal of the project is to  implement and analyse the performance , limits of a method of improving the stability of the GAN's training:  Using an MMD as a critic.
# Quelques notes
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
