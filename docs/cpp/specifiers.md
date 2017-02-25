---
title: "Especificadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "especificadores de declaración"
  - "declaraciones, especificadores"
  - "especificadores, en declaraciones"
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Especificadores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describe el componente *decl\-specifiers* \(especificadores de declaración\) de una [declaración](../misc/declarations.md).  
  
 Los siguientes marcadores de posición y palabras clave de lenguaje son especificadores de declaración:  
  
 *storage\-class\-specifier*  
  
 *type\-specifier*  
  
 *function\-specifier*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/es-es/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [\_\_declspec](../cpp/declspec.md) `(` *extended\-decl\-modifier\-seq* `)`  
  
## Comentarios  
 La parte de*decl\-specifiers* de una declaración es la secuencia más larga de *decl\-specifiers* que se puede tomar para indicar un nombre de tipo, sin incluir los modificadores de puntero o de referencia.  El resto de la declaración es la parte de *declarator*, que incluye el nombre introducido.  
  
 La tabla siguiente incluye cuatro declaraciones y enumera los componentes de *decl\-specifers* y *declarator* de cada declaración por separado.  
  
|Declaración|*decl\-specifiers*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 Dado que `signed`, `unsigned`, `long` y `short` implican `int`, un nombre de `typedef` seguido de una de estas palabras clave se considera como miembro de *declarator\-list*, no de *decl\-specifiers*.  
  
> [!NOTE]
>  Dado que un nombre se puede declarar de nuevo, su interpretación está sujeta a la declaración más reciente del ámbito actual.  La nueva declaración puede afectar al modo en que el compilador interpreta los nombres, especialmente los nombres de `typedef`.  
  
## Vea también  
 [Declaraciones](../misc/declarations.md)