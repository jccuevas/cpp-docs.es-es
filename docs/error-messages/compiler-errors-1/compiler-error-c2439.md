---
title: "Error del compilador C2439 | Microsoft Docs"
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
  - "C2439"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2439"
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2439
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no se pudo inicializar el miembro  
  
 No se pudo inicializar un miembro de una clase, estructura o unión.  
  
### Posibles causas del error:  
  
1.  Se intenta inicializar una clase base o estructura indirecta.  
  
2.  Se intenta inicializar un miembro heredado de una clase o estructura.  Un miembro heredado debe ser inicializado por el constructor de la clase o estructura.