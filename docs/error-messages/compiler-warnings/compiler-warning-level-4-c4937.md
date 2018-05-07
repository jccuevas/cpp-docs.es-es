---
title: Compilador advertencia (nivel 4) C4937 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed7b33889677a304d303873799f36430c38129a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4937"></a>Advertencia del compilador (nivel 4) C4937
'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'  
  
 Debido a la forma en que el compilador procesa argumentos para directivas, no es posible distinguir los nombres que tienen un significado para el compilador como, por ejemplo, palabras clave con varias representaciones de texto (en formato de subrayado simple y doble).  
  
 Algunos ejemplos de estas cadenas son __cdecl y \__forceinline.  Tenga en cuenta que con /Za solo se habilita el formato de subrayado doble.  
  
 El ejemplo siguiente genera la advertencia C4937:  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```