---
title: "Error del compilador C2500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2500"
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2500
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador1' : 'identificador2' ya es una clase base directa  
  
 Una clase o estructura aparece más de una vez en una lista de clases base.  
  
 Una base directa es una mencionada en la lista base.  Una base indirecta es una clase base de alguna de las clases que componen la lista base.  
  
 Una clase no se puede especificar como clase base directa más de una vez.  Una clase no se puede utilizar como clase base indirecta más de una vez.  
  
 El código siguiente genera el error C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```