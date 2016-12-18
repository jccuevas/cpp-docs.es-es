---
title: "Error del compilador C2597 | Microsoft Docs"
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
  - "C2597"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2597"
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2597
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

referencia no válida a miembro no estático 'identifier'  
  
 Causas posibles:  
  
1.  Se especifica un miembro no estático en una función de miembro estático.  Para tener acceso al miembro no estático, debe pasar o crear una instancia local de la clase y usar un operador de acceso a miembros \(`.` o `->`\).  
  
2.  El identificador especificado no es miembro de una clase, estructura o unión.  Revisar la ortografía del identificador.  
  
3.  Un operador de acceso a miembros hace referencia a una función no miembro.  
  
4.  El ejemplo siguiente genera el error C2597 y muestra cómo corregirlo:  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
  
```