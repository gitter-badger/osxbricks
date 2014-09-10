---
layout: post
title:  "Ecouter la radio avec Alfred"
date:   2014-07-02 22:59:35
categories: Alfred_Workflow
---

**[Radio](http://inft.ly/4qFB2Sc)** permet d'écouter des webradios sur votre application de musique préférée, comme [iTunes](https://www.apple.com/itunes/) ou [VLC](http://www.videolan.org/index.fr.html). Ce workflow est pour les utilisateurs du [Powerpack](http://www.alfredapp.com/powerpack/) d'[Alfred](http://www.alfredapp.com).

<img src="http://cl.ly/image/2E0P210R4204/radioWorkflow.gif" width="834" height="615" alt="Démonstatrion : radio avec alfred" class="aligncenter" />

## Radio vous permet d':

- **écouter 35 stations** par défaut via `radio {name}`,
- **ajouter vos propres stations** via `radioadd {flux} {name}`,
- supprimer une station via `radiorm {name}`,
- retrouver la configuration par défaut `radioreset`,

N'hésitez pas à commenter ou envoyer un <a href="mailto:contact@osxbricks.com">mail</a> pour **proposer des radios** à ajouter par défaut ! 

## Dévloppement

Ce workflow est mon premier  projet en Python. Pour communiquer facilement avec  **Alfred** , j'ai utilisé la librairie [alp de Daniel Shannon](https://github.com/phyllisstein/alp), et enlever certains composant inutile (pour ce workflow) pour améliorer sa vitesse.