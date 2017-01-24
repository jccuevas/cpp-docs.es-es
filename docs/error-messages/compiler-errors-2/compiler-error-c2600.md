---
title: "Error del compilador C2600 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2600"
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': no se puede definir una función miembro especial generada por el compilador \(se debe declarar primero en la clase\)  
  
 Antes de que se puedan definir funciones miembro, como constructores o destructores, para una clase, se deben declarar en la clase.  Si no se declaran en la clase, el compilador puede generar constructores y destructores predeterminados \(lo que se conoce como funciones miembro especiales\).  Sin embargo, si define una de estas funciones sin una declaración coincidente en la clase, el compilador detecta un conflicto.  
  
 Para corregir este error, en la declaración de clase, declare cada función miembro que defina fuera de la declaración de clase.  
  
 El código siguiente genera el error C2600:  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```