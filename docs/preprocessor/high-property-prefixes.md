---
title: "high_property_prefixes | Microsoft Docs"
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
  - "high_property_prefixes"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "high_property_prefixes (atributo)"
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# high_property_prefixes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## Sintaxis  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### Parámetros  
 `GetPrefix`  
 Prefijo que se usará para los métodos **propget**.  
  
 `PutPrefix`  
 Prefijo que se usará para los métodos **propput**.  
  
 `PutRefPrefix`  
 Prefijo que se usará para los métodos **propputref**.  
  
## Comentarios  
 De forma predeterminada, los métodos **propget**, **propput** y **propputref** de control de errores de alto nivel son expuestos por funciones miembro denominadas con los prefijos **Get**, `Put` y **PutRef**, respectivamente.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)