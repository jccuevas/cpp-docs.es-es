---
title: Atomic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e9e9ecad2f6ea53e2f922799340eee47dd4a7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037494"
---
# <a name="atomic"></a>atómico
Especifica que una ubicación de memoria que se actualizarán de forma atómica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>Parámetros  
*Expresión*<br/>
La instrucción que contiene el valor de l cuya ubicación de memoria que desea proteger contra varias escrituras. Para obtener más información acerca de los formularios de expresión legal, consulte la especificación OpenMP.  
  
## <a name="remarks"></a>Comentarios  
 El `atomic` directiva es compatible con ningún cláusulas de OpenMP.  
  
 Para obtener más información, consulte [2.6.4 atomic construir](../../../parallel/openmp/2-6-4-atomic-construct.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
```Output  
Number of threads: 10  
```  
  
## <a name="see-also"></a>Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)