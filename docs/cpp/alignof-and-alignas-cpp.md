---
title: "alignof y alignas (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# alignof y alignas (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El especificador de tipo `alignas` es una manera portátil y estándar de C\+\+ de especificar una alineación personalizada de variables y tipos definidos por el usuario.  El operador `alignof` también es una forma estándar y portátil de obtener la alineación de una variable o un tipo especificado.  
  
## Ejemplo  
 Puede usar `alignas` en una clase, struct o union, o en miembros individuales.  Cuando varios especificadores de `alignas` se encuentran, el compilador elige el más estricto \(el que tiene el valor más grande\).  
  
```  
struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  
…  
cout << alignof(Bar) << endl; // output: 16  
  
```  
  
## Vea también  
 [Alineación](../cpp/alignment-cpp-declarations.md)