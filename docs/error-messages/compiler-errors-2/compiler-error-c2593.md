---
title: Error del compilador C2593 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2593
dev_langs: C++
helpviewer_keywords: C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 675c929995e7b0c4043586cf081343136d8e7a5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2593"></a>Error del compilador C2593
'identifier' operador' es ambiguo  
  
 Más de un posible operador está definido para un operador sobrecargado.  
  
 Este error puede corregirse si utiliza una conversión explícita en uno o varios parámetros reales.  
  
 El ejemplo siguiente genera C2593:  
  
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
  
 Este error puede deberse a un punto flotante por medio de serializar un `CArchive` objeto. El compilador identifica la `<<` operador como ambigua. Tipos de C++ solo primitivos que `CArchive` puede serializar son los tipos de tamaño fijo `BYTE`, `WORD`, `DWORD`, y `LONG`. Todos los tipos de entero se deben convertir a uno de estos tipos para la serialización. Tipos de punto flotante pueden almacenarse utilizando la `CArchive::Write()` función miembro.  
  
 En el ejemplo siguiente se muestra cómo almacenar una variable de punto flotante (`f`) al archivo `ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```