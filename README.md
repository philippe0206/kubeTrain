# kube
------
Gestion d un reseau train electrique
_-------------------------------------
SOFTWARE : un Kube = 1 container = 1 fonction
HARDWARE : un Pod = 1 Device + 1 Module
POD
_---
   HardWare
      1 Module
         Type : arduino+wifi , Pi ...
      1 device 
         Type : lampe relais  moteur DetecteurOnOff DetecteurTension TensionProgrammable TensionFixe ...
   interface
      web privé POD <---> KubeBaseInfra     
      rootShell
_------------------------------------
KubeBase
_-------
  interface
      web privé POD <---> KubeBaseInfra
      web public KubeBase <---> {Kube*,..}   
      rootShell
  Famille
   KubeBaseInfra_
   _-----------
   controle un POD 
      Type: signal , canton , aiguillage, moteur, relais, lampe ,PlaqueTournante , voie...      
         Exemple Type : Signal            = Pod ( 3 feux )
         Exemple Type : PlaqueTournante   = Pod ( 1 MoteurStepper ,  12 DetecteurOnOff )
   KubeBaseRuner
   _-----------
   controle un materiel roulant 
      Type: KubeBaseInfra_locomotive , KubeBaseInfra_wagon  
         Exemple Type : Locomotive  = Pod_Moteur 
         Exemple Type : Train       = 1 KubeBaseRuner_locomotive + 5 KubeBaseRuner_wagonsMarchandises 
   KubeBasePoste
   _-----------
   controle un groupe fonctionnel
      Type :Jonction , voie , canton ..
         Exemple Type: Jonction  = 1 KubeBaseInfra_aiguillage + 1 signal 
         Exemple Type: voie      = 1 KubeBaseInfra_voie PK1----PK2
         Exemple Type: canton    = 1 KubeBaseInfra_voie + 1 KubeBaseInfra_signal
   KubeBaseLocal
   _-----------
   controle un groupe geographique
      Type: gare , rotonde , gare de triage ...
      Exemple Type : gare        = 2 KubeBasePoste_Jonction + 2 KubeBasePoste_canton + 2 KubeBasePoste_voie
      Exemple Type : rotonde     = 1 KubeBaseInfra_PlaqueTournante + 12 KubeBasePoste_canton
_------------------------------------ 
KubeTrantor
_-----------
  contient
    shell de commande
        ChefDeGare# :  TrainCharbon VA MineCharbon 
        ChefDeGare# :  TrainCharbon = assemble( LocoBB1091, VagonCiterne40T , VagonCiterne40T , VagonCiterne40T , VagonCiterne40T ) 
Kube-1Fondation
_-----------
  contient
    interface web html
    DB 
      Convois
         KubeBaseRuner_tain      
      regles de fonctionnement
         Exemple :    SignalRouge , Distance entre les convois
      scripts
         Exemple :    Express_Paris_Lyon , Omnibus_BretagneNord    
Kube_2Fondation
_-----------
  controle activite des KubeBase & entre les KubeBase
  interface web html
    contient 
      monitoring
      supervision
