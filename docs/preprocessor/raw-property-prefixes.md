---
title: "raw_property_prefixes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_property_prefixes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_property_prefixes (atributo)"
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_property_prefixes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## Sintaxis  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### Parámetros  
 `GetPrefix`  
 Prefijo que se usará para los métodos **propget**.  
  
 `PutPrefix`  
 Prefijo que se usará para los métodos **propput**.  
  
 `PutRefPrefix`  
 Prefijo que se usará para los métodos **propputref**.  
  
## Comentarios  
 De forma predeterminada, los métodos **propget**, **propput** y **propputref** de bajo nivel son expuestos por funciones miembro que incluyen en sus nombres los prefijos **get\_**, **put\_** y **putref\_**, respectivamente.  Estos prefijos son compatibles con los nombres que se usan en los archivos de encabezado generados por MIDL.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)