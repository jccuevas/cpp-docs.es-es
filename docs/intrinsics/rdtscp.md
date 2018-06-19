---
title: __rdtscp | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d890afe9e19782f19442e8d95709b91a8680278
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329808"
---
# <a name="rdtscp"></a>__rdtscp
**Específicos de Microsoft**  
  
 Genera el `rdtscp` escribe instrucciones, `TSC_AUX[31:0`] a la memoria y devuelve el contador de marca de tiempo de 64 bits (`TSC)` resultado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `Aux`  
 Puntero a una ubicación que contiene el contenido del Registro específicas del equipo `TSC_AUX[31:0]`.  
  
## <a name="return-value"></a>Valor devuelto  
 Un contador de entero sin signo de 64 bits.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__rdtscp`|Familia de AMD NPT 0Fh o versiones posteriores|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función intrínseca genera el `rdtscp` instrucción. Para determinar la compatibilidad de hardware con esta instrucción, llame a la `__cpuid` intrínseco con `InfoType=0x80000001` y comprobar bit 27 de `CPUInfo[3] (EDX)`. Este bit es 1 si se admite la instrucción y 0 en caso contrario.  Si ejecuta el código que usa esta función intrínseca en hardware que no es compatible con la `rdtscp` instrucciones, los resultados son imprevisibles.  
  
> [!CAUTION]
>  A diferencia de `rdtsc`, `rdtscp` es una instrucción de serialización; no obstante, el compilador puede mover código alrededor de esta función intrínseca.  
  
 La interpretación del valor TSC en esta generación de hardware difiere del comportamiento en las versiones anteriores de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Consulte los manuales de hardware para obtener más información.  
  
 El significado del valor de `TSC_AUX[31:0]` depende del sistema operativo.  
  
## <a name="example"></a>Ejemplo  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
```Output  
3363423610155519 ticks  
TSC_AUX was 0  
```  
  
**FIN de Específicos de Microsoft**  
 Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Vea también  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)