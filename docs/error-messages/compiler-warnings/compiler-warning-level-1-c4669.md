---
title: Compilador advertencia (nivel 1) C4669 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4669
dev_langs: C++
helpviewer_keywords: C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 203650a0d1e53fe9e13ca6dae58dfa3d0a42e4ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4669"></a>Advertencia del compilador (nivel 1) C4669
'cast': conversión no segura: 'class' es un objeto de tipo administrado o WinRT  
  
 Una conversión contiene un tipo administrado o de Windows Runtime. El compilador completa la conversión con una copia bit a bit de un puntero a otro, pero no realiza ninguna otra comprobación. Para resolver esta advertencia, no convierta las clases que contienen miembros administrados o tipos de Windows en tiempo de ejecución.  
  
 El ejemplo siguiente genera el error C4669 y muestra cómo corregirlo:  
  
```  
// C4669.cpp  
// compile with: /clr /W1  
ref struct A {  
   int i;  
   Object ^ pObj;   // remove the managed member to fix the warning  
};  
  
ref struct B {  
   int j;  
};  
  
int main() {  
   A ^ a = gcnew A;  
   B ^ b = reinterpret_cast<B ^>(a);   // C4669  
}  
```