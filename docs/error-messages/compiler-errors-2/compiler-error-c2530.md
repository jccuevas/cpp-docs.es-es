---
title: Error del compilador C2530 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f9438937ad99e66d9e623e1e3703dc6496f8153a
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2530"></a>Error del compilador C2530
'identificador': se deben inicializar las referencias  
  
 Debe inicializar una referencia cuando se ha declarado, a menos que ya se haya declarado:  
  
-   Con la palabra clave [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   Como miembro de una clase, estructura o unión (y se inicializa en el constructor).  
  
-   Como un parámetro en una definición o declaración de función.  
  
-   Como el tipo de valor devuelto de una función.  
  
 El ejemplo siguiente genera C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```
