---
title: Error del compilador C3012 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d30a7fbb50a984c8cec6b45a0ab4759a0578de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3012"></a>Error del compilador C3012
  
> '*intrínseco*': función intrínseca no permitida directamente dentro de una región paralela  
  
 Una función [intrínseca del compilador](../../intrinsics/compiler-intrinsics.md) no se permite en una región `omp parallel` . Para corregir este problema, mueva intrínsecos fuera de la región o reemplácelos por no intrínseco equivalentes.   
  
## <a name="example"></a>Ejemplo  
  
 El ejemplo siguiente genera la advertencia C3012 y muestra una forma de corregirlo:  
  
```cpp  
// C3012.cpp  
// compile with: /openmp  
#ifdef __cplusplus  
extern "C" {  
#endif  
void* _ReturnAddress();  
#ifdef __cplusplus  
}  
#endif  
  
int main()  
{  
   #pragma omp parallel  
   {  
      _ReturnAddress();   // C3012  
   }  
   _ReturnAddress();      // OK  
}  
```