---
title: "raw_interfaces_only | Microsoft Docs"
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
  - "raw_interfaces_only"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_interfaces_only (atributo)"
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_interfaces_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Suprime la generación de funciones de contenedor para control de errores y las declaraciones [propiedad](../cpp/property-cpp.md) que utilizan esas funciones de contenedor.  
  
## Sintaxis  
  
```  
raw_interfaces_only  
```  
  
## Comentarios  
 El atributo `raw_interfaces_only` también hace que se quite el prefijo predeterminado utilizado en la nomenclatura de las funciones que no son de propiedad.  Normalmente, el prefijo es **raw\_**.  Si se especifica este atributo, los nombres de función pertenecen directamente a la biblioteca de tipos.  
  
 Este atributo permite exponer solo el contenido de bajo nivel de la biblioteca de tipos.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)