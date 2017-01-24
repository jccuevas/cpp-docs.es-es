---
title: "Error del compilador C2584 | Microsoft Docs"
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
  - "C2584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2584"
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'Clase' : base directa 'Base2' no es accesible; ya existe una base de 'Base1'  
  
 `Class` ya se deriva directamente de `Base1`.  `Base2` también se deriva de `Base1`.  `Class` no se puede derivar de `Base2` ya que eso significaría heredar \(indirectamente\) de `Base1` una vez más, que no es legal puesto que `Base1` ya es una clase base directa.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2584.  
  
```  
// C2584.cpp  
// compile with: /c  
struct A1 {  
   virtual int MyFunction();  
};  
  
struct A2 {  
    virtual int MyFunction();  
};  
  
struct B1: public virtual A1, virtual A2 {  
    virtual int MyFunction();  
};  
  
struct B2: public virtual A2, virtual A1 {  
    virtual int MyFunction();  
};  
  
struct C: virtual B1, B2 {  
    virtual int MyFunction();  
};  
  
struct Z : virtual B2, virtual C {   // C2584  
// try the following line insted  
// struct Z : virtual C {  
    virtual int MyFunction();  
};  
```