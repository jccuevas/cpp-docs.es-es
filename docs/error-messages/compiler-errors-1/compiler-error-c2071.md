---
title: "Error del compilador C2071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2071"
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': clase de almacenamiento no válida  
  
 `identifier` se ha declarado con una etiqueta de [clase de almacenamiento](../../c-language/c-storage-classes.md) no válida.  Este error puede producirse cuando se especifica más de una clase de almacenamiento para un identificador, o cuando la definición no es compatible con la declaración de clase de almacenamiento.  
  
 Para corregir este problema, averigüe la clase de almacenamiento previsto del identificador \(por ejemplo, `static` o  `extern`\) y corrija la declaración con la que debe coincidir.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2071.  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2071.  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```