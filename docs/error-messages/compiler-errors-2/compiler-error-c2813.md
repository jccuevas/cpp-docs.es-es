---
title: "Error del compilador C2813 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2813"
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se admite \#import con \/MP  
  
 El error C2813 se genera si en un comando de compilador se especifica la opción del compilador **\/MP** y dos o más archivos para compilar y uno o varios de los archivos contiene la directiva de preprocesador [\#import](../../preprocessor/hash-import-directive-cpp.md). La directiva [\#import](../../preprocessor/hash-import-directive-cpp.md) genera clases de C\+\+ a partir de los tipos de la biblioteca de tipos especificada y, a continuación, escribe las clases en dos archivos de encabezado. La directiva [\#import](../../preprocessor/hash-import-directive-cpp.md) no se admite la directiva porque si varias unidades de compilación importan la misma biblioteca de tipos, las unidades entran en conflicto al intentar escribir los mismos archivos de encabezado al mismo tiempo.  
  
 Este error del compilador y la opción del compilador **\/MP** son nuevas en [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)].  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2813. La línea de comandos del comentario "compile with:" indica al compilador que debe usar las opciones del compilador **\/MP** y **\/c** para compilar varios archivos. Al menos uno de los archivos contiene la directiva [\#import](../../preprocessor/hash-import-directive-cpp.md). El mismo archivo se usa dos veces para probar este ejemplo.  
  
```  
// C2813.cpp // compile with: /MP /c C2813.cpp C2813.cpp #import "C:\windows\system32\stdole2.tlb"   // C2813 int main() { }  
```