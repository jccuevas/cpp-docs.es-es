---
title: "Leer intervalos | Microsoft Docs"
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
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Leer intervalos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.9.6.2** La interpretación de un carácter de guion \(–\) que no sea el primero ni el último carácter de scanlist para la conversión % \[ en la función `fscanf`  
  
 La línea siguiente  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 lee cualquier número de caracteres del intervalo A – Z en la cadena a la que `strptr` señala.  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)