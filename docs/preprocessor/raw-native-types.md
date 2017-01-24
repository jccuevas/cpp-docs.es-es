---
title: "raw_native_types | Microsoft Docs"
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
  - "raw_native_types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_native_types (atributo)"
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_native_types
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Deshabilita el uso de las clases de soporte de COM en las funciones de contenedor de alto nivel y, en su lugar, fuerza el uso de tipos de datos de bajo nivel.  
  
## Sintaxis  
  
```  
raw_native_types  
```  
  
## Comentarios  
 De forma predeterminada, los métodos de control de errores de alto nivel utilizan las clases de soporte COM [\_bstr\_t](../cpp/bstr-t-class.md) y [\_variant\_t](../cpp/variant-t-class.md) en lugar de los tipos de datos `BSTR` y **VARIANT**, y punteros sin formato de interfaz COM.  Estas clases encapsulan los detalles de asignación y desasignación del almacenamiento de memoria para estos tipos de datos, y simplifican considerablemente la conversión de tipos y las operaciones de conversión.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)