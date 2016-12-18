---
title: "Error de la optimizaci&#243;n guiada por perfiles PG0165 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PG0165"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PG0165"
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de la optimizaci&#243;n guiada por perfiles PG0165
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Leyendo 'NombreArchivo.pgd' : "Versión de PGD incompatible \(la versión no coincide\)".  
  
 Los archivos PGD son específicos de un conjunto de herramientas de un compilador en concreto.  Este error se genera cuando está utilizando un compilador distinto del que se utiliza para *Filename*.pgd.  Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.  
  
 Para resolver este problema, *Filename*regenerar .pgd con el conjunto de herramientas del compilador actual.