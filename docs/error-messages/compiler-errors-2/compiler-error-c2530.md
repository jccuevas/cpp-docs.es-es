---
title: Error del compilador C2530 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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