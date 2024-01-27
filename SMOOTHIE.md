---
title: $\beta-$smoothness as a heuristic for HPO
date: 2023-04-21
id: 20230421175738
author: Rahul Yedida
---
#theoretical-ml #hpo #beta-smoothness

# Smoothness as a heuristic for HPO

In a recent paper [@yedidaSMOOTHIETheoryHyperparameter], we proposed using the $\beta-$smoothness (see [[beta-smoothness]]) of the loss function as a heuristic for HPO. Although a higher value of $\beta-$smoothness means more fluctuations, we found that in practice, this translated to a flat minima with sharp corners, and the optimizer was able to find the flat minima (which generalizes better). This work was motivated by [@yedidaHowFindActionable2023] (see [[Better data preprocessing]] for a discussion), who showed that their preferred techniques yielded a smoother loss landscape.