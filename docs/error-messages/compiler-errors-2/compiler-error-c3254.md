---
title: Error del compilador C3254 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3254
dev_langs: C++
helpviewer_keywords: C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 104ee89c45d8a1134611535ab6aa9c62f09e139c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3254"></a>Error del compilador C3254
'reemplazo explícito': clase contiene el reemplazo explícito 'reemplazo' pero no se deriva de una interfaz que contiene la declaración de función  
  
 Cuando se [reemplazar explícitamente](../../cpp/explicit-overrides-cpp.md) un método, la clase que contiene el reemplazo debe derivarse, directa o indirectamente, del tipo que contiene la función se va a reemplazar.  
  
 El ejemplo siguiente genera C3254:  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```