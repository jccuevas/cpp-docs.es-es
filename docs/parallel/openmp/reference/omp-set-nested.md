---
title: omp_set_nested () | Microsoft Docs
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
ms.openlocfilehash: fc3506c35dca469febafe21509064abc1726d633
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116904"
---
# <a name="ompsetnested"></a>omp_set_nested
Habilita el paralelismo anidado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
### <a name="parameters"></a>Parámetros
  
*Val*<br/>
Si es distinto de cero, habilita el paralelismo anidado. Si es cero, deshabilita el paralelismo anidado.  
  
## <a name="remarks"></a>Comentarios  
 OMP anidado paralelismo puede activarse con `omp_set_nested`, o estableciendo la [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md) variable de entorno.  
  
 La configuración de `omp_set_nested` reemplazará la configuración de la `OMP_NESTED` variable de entorno.  
  
 Cuando se habilita, la variable de entorno puede interrumpir un programa operativo en caso contrario, ya que aumenta exponencialmente el número de subprocesos cuando se anidan regiones en paralelo.  Por ejemplo, una función que recorre 6 veces con el número de subprocesos OMP establecido en 4 requiere 4096 (4 a la potencia de 6) de subprocesos en general, se degradará el rendimiento de la aplicación si el número de subprocesos supera el número de procesadores. Una excepción a esto sería que aplicaciones enlazadas con E/S.  
  
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