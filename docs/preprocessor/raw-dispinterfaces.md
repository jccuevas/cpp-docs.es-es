---
title: "raw_dispinterfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_dispinterfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_dispinterfaces (atributo)"
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_dispinterfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Indica al compilador que genere funciones de contenedor de bajo nivel para los métodos y propiedades dispinterface que llamen a **IDispatch::Invoke** y devuelvan el código de error `HRESULT`.  
  
## Sintaxis  
  
```  
raw_dispinterfaces  
```  
  
## Comentarios  
 Si no se especifica este atributo, solo se generan los contenedores de alto nivel, que inician excepciones de C\+\+ en caso de error.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)