---
title: "virtual (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "virtual_cpp"
  - "virtual"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases base, virtual"
  - "clases base virtuales, declarar"
  - "funciones virtuales, declarar"
  - "virtual (palabra clave) [C++]"
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# virtual (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `virtual` declara una función virtual o una clase base virtual.  
  
## Sintaxis  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### Parámetros  
 `type-specifiers`  
 Especifica el tipo de valor devuelto de la función miembro virtual.  
  
 `member-function-declarator`  
 Declara una función miembro.  
  
 `access-specifier`  
 Define el nivel de acceso a la clase base: `public`, `protected` o `private`.  Puede aparecer antes o después de la palabra clave `virtual`.  
  
 `base-class-name`  
 Identifica un tipo de clase declarado previamente.  
  
## Comentarios  
 Vea [Funciones virtuales](../cpp/virtual-functions.md) y [Clases base virtuales](../misc/virtual-base-classes.md) para obtener más información.  
  
 Vea también las siguientes palabras clave: [class](../cpp/class-cpp.md), [private](../cpp/private-cpp.md), [public](../cpp/public-cpp.md) y [protected](../cpp/protected-cpp.md).  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)