---
title: Error del compilador C2563 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2563
dev_langs: C++
helpviewer_keywords: C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8fe3ca54a90b91151288076fd657752e3195e318
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2563"></a>Error del compilador C2563
Error de coincidencia en la lista de parámetros formales  
  
 La lista de parámetros formales de una función (o un puntero a una función) no coincide con los de otra función (o puntero a una función miembro). Como resultado, no se puede realizar la asignación de funciones o punteros.  
  
 El ejemplo siguiente genera C2563:  
  
```  
// C2563.cpp  
void func( int );  
void func( int, int );  
int main() {  
   void *fp();  
   fp = func;   // C2563  
}  
```