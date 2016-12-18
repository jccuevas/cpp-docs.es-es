---
title: "tlbid | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tlbid"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tlbid (atributo)"
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tlbid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.  
  
## Sintaxis  
  
```  
tlbid(number)  
```  
  
#### Parámetros  
 `number`  
 Número de la biblioteca de tipos en `filename`.  
  
## Comentarios  
 Si hay varias bibliotecas de tipos compiladas en un mismo archivo DLL, se pueden cargar bibliotecas distintas de la biblioteca de tipos principal mediante `tlbid`.  
  
 Por ejemplo:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 equivale a:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)