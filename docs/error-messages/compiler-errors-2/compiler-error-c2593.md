---
title: "Error del compilador C2593 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2593"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2593"
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2593
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador identificador' es ambiguo  
  
 Hay más de un posible operador definido para un operador sobrecargado.  
  
 Podrá corregir este error si utiliza una conversión explícita en uno o varios parámetros reales.  
  
 El código siguiente genera el error C2593:  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 Puede producirse este error si se serializa una variable de punto flotante mediante un objeto `CArchive`.  El compilador identifica el operador `<<` como ambiguo.  Los únicos tipos de C\+\+ primitivos que `CArchive` puede serializar son los tipos de tamaño fijo `BYTE`, `WORD`, `DWORD` y `LONG`.  Todos los tipos enteros deben convertirse a uno de estos tipos para la serialización.  Los tipos de punto flotante pueden almacenarse utilizando la función miembro `CArchive::Write()`.  
  
 El código siguiente muestra cómo almacenar una variable de punto flotante \(`f`\) para almacenar `ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```