---
title: "Acceso incorrecto a una uni&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acceso incorrecto a una uni&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3.2.3** El acceso a un objeto de unión se realiza mediante un miembro de tipo diferente  
  
 Si se declara una unión de dos tipos y se almacena un valor, pero se obtiene acceso a la unión con el otro tipo, los resultados no son confiables.  
  
 Por ejemplo, se declara una unión de **float** e `int`.  Se almacena un valor **float**, pero el programa obtiene acceso posteriormente al valor como `int`.  En esta situación, el valor dependería del almacenamiento interno de los valores **float**.  El valor entero no sería confiable.  
  
## Vea también  
 [Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)