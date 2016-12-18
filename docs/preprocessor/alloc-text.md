---
title: "alloc_text | Microsoft Docs"
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
  - "vc-pragma.alloc_text"
  - "alloc_text_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "alloc_text (pragma)"
  - "pragma (directivas), alloc_text"
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alloc_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa la sección de código donde residirán las definiciones de función especificadas.  La directiva pragma debe aparecer entre un declarador de función y la definición de función para las funciones designadas.  
  
## Sintaxis  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## Comentarios  
 La directiva pragma **alloc\_text** no controla funciones miembro de C\+\+ o funciones sobrecargadas.  Solo es aplicable a las funciones declaradas con vinculación de C \(es decir, funciones declaradas con la especificación de vinculación **extern de "C"**\).  Si intenta utilizar esta directiva pragma en una función con vinculación de C\+\+, se genera un error del compilador.  
  
 Puesto que el direccionamiento de la función mediante `__based` no se admite, especificar ubicaciones de sección requiere el uso de la directiva pragma **alloc\_text**.  El nombre especificado por *textsection* se debe incluir entre comillas dobles.  
  
 La directiva pragma **alloc\_text** debe aparecer después de las declaraciones de las funciones especificadas y antes de las definiciones de estas funciones.  
  
 Las funciones a las que se hace referencia en una directiva pragma **alloc\_text** se deben definir en el mismo módulo que la directiva pragma.  Si no es así y después se compila una función sin definir en otra sección de texto, el error se puede detectar o no.  Aunque lo normal es que el programa se ejecute correctamente, la función no se asignará en las secciones previstas.  
  
 Estas son otras de las limitaciones de **alloc\_text**:  
  
-   No se puede utilizar dentro de una función.  
  
-   Debe utilizarse una vez declarada la función, pero antes de que esta se haya definido.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)