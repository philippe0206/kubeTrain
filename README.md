# kube
------
Gestion d un reseau train electrique
-------------------------------------
un Kube = 1 container = 1 fonction
un Pod = 1 Device + 1 arduino

=====================================
POD
---
   HardWare
      1 arduino+wifi
      1 device lampe relais  moteur
   interface
      web privé POD <---> KubeBaseInfra
      
=====================================
KubeBase
--------
  interface
      web privé POD <---> KubeBaseInfra
      web public KubeBase <---> {KubeBase}     
  Famille
   KubeBaseInfra_
   -------------
   controle un POD 
      Type: signal , canton , aiguillage, moteur, relais, lampe ,laqueTournante , voie...      
   KubeBaseRuner
   -------------
   controle un materiel roulant 
      Type: KubeBaseInfra_locomotive , KubeBaseInfra_wagon  
      Type: Train = 1 KubeBaseRuner_locomotive + 5 KubeBaseRuner_wagonsMarchandises 
   KubeBasePoste
   -------------
   controle un groupe fonctionnel
      Type: Jonction =  1 KubeBaseInfra_aiguillage + 1 signal 
      Type: voie = 1 KubeBaseInfra_voie PK1----PK2
      Type: canton = 1 KubeBaseInfra_voie + 1 KubeBaseInfra_signal
   KubaseLocal
   -----------
   controle un groupe geographique
      Type: gare , rotonde , gare de triage ...
      Type : gare = 2 KubeBasePoste_Jonction + 2 KubeBasePoste_canton + 2 KubeBasePoste_voie
      Type : rotonde = 1 KubeBaseInfra_PlaqueTournante + 12 KubeBasePoste_canton
      
=====================================      
KubeTrantor
-----------
  contient
    shell de commande
        ex TrainCharbon VA MineCharbon 
Kube-1Fondation
---------------
  contient
    DB 
      regles de fonctionnement
        ex SignalRouge , Distance entre les convois
      scripts
        ex Express_Paris_Lyon , Omnibus_BretagneNord    
Kube_2Fondation
---------------
  controle activite des & entre les KubeBase
  interface web html
    contient 
      monitoring
      supervision
