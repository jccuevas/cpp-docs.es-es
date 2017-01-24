---
title: "Error del compilador C2914 | Microsoft Docs"
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
  - "C2914"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2914"
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2914
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no se puede deducir el argumento de tipo, ya que el argumento de función es ambiguo  
  
 El compilador no puede determinar qué funciones sobrecargadas utilizar con un argumento genérico o de plantilla.  
  
 El código siguiente genera el error C2914:  
  
```  
// C2914.cpp  
// compile with: /c  
void f(int);  
void f(double);  
template<class T> void g(void (*) (T));  
void h() { g(f); }   // C2914  
// try the following line instead  
// void h() { g<int>(f); }  
```  
  
 El error C2914 también puede producirse cuando se utilizan genéricos.  El código siguiente genera el error C2914:  
  
```  
// C2914b.cpp  
// compile with: /clr /c  
void f(int);  
void f(double);  
  
template<class T>   
void gf(void (*) (T));  
  
void h() { gf(f);}   // C2914  
// try the following line instead  
void h() { gf<int>(f); }  
```