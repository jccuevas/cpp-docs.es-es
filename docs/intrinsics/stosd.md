---
title: __stosd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosd
dev_langs:
- C++
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f019a0c2c62b991b2799f1a5d6d89402054c0260
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723390"
---
# <a name="stosd"></a>__stosd
**Específicos de Microsoft**  
  
 Genera una instrucción de cadena de la tienda (`rep stosd`).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __stosd(   
   unsigned long* Dest,   
   unsigned long Data,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
*dest*<br/>
[out] El destino de la operación.  
  
*Data*<br/>
[in] Para almacenar los datos.  
  
*Recuento*<br/>
[in] La longitud del bloque de palabras dobles para escribir.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__stosd`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El resultado es que la palabra doble `Data` se escribe en un bloque de `Count` palabras dobles en la ubicación de memoria a la que señala a `Dest`.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
```  
// stosd.c  
// processor: x86, x64  
  
#include <stdio.h>  
#include <memory.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosd)  
  
int main()  
{  
    unsigned long val = 99999;  
    unsigned long a[10];  
  
    memset(a, 0, sizeof(a));  
    __stosd(a+1, val, 2);  
  
printf_s( "%u %u %u %u",  
              a[0], a[1], a[2], a[3]);   
}  
```  
  
```Output  
0 99999 99999 0  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)