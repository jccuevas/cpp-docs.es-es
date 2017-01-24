---
title: "Restricciones de la funci&#243;n main | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Main"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "main (función), restricciones de uso"
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Restricciones de la funci&#243;n main
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A la función **main** se le aplican varias restricciones que no se aplican a otras funciones de C\+\+.  La función **main**:  
  
-   No se puede sobrecargar \(vea [Sobrecarga](../misc/overloading-cpp.md)\).  
  
-   No se puede declarar como **inline**.  
  
-   No se puede declarar como **static**.  
  
-   No se puede tomar su dirección.  
  
-   No se puede llamar.  
  
## Vea también  
 [main: inicio de programa](../cpp/main-program-startup.md)