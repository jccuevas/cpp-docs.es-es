---
title: "Error del compilador C2785 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2785"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2785"
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2785
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaración1' y 'declaración2' tienen distintos tipos de valor devueltos  
  
 El tipo de valor devuelto de una especialización de plantilla de función se diferencia del tipo de valor devuelto de la plantilla de función primaria.  
  
### Para corregir este error  
  
1.  Compruebe todas las especializaciones de la plantilla de función a efectos de coherencia.  
  
## Ejemplo  
 El código siguiente genera el error C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```