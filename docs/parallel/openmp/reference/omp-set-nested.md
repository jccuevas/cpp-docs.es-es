---
title: omp_set_nested () | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6539167b936efdc4c9f407cd951c9c582b0a138
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetnested"></a>omp_set_nested
Habilita el paralelismo anidado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `val`  
 Si es distinto de cero, habilita el paralelismo anidado. Si es cero, deshabilita paralelismo anidado.  
  
## <a name="remarks"></a>Comentarios  
 OMP anidado pueden activar paralelismo con `omp_set_nested`, o estableciendo la [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) variable de entorno.  
  
 La configuración de `omp_set_nested` sobrescribirá la configuración de la `OMP_NESTED` variable de entorno.  
  
 Cuando se habilita, la variable de entorno puede interrumpir un programa operativo en caso contrario, porque el número de subprocesos aumenta exponencialmente cuando se anidan regiones en paralelo.  Por ejemplo, una función que recorre 6 veces con el número de subprocesos OMP establecido en 4 requiere 4096 (4 a la potencia de 6) subprocesos por lo general, el rendimiento de la aplicación se verá afectado si el número de subprocesos supera el número de procesadores. Una excepción a esto sería que e/s enlaza las aplicaciones.  
  
 Use [omp_get_nested ()](../../../parallel/openmp/reference/omp-get-nested.md) para mostrar la configuración actual de `omp_set_nested`.  
  
 Para obtener más información, consulte [3.1.9 omp_set_nested (función)](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)