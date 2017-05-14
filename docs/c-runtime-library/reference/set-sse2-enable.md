---
title: _set_SSE2_enable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_SSE2_enable
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
dev_langs:
- C++
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6dcc32b981c73cda13152f82139a307e4739fe5c
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="setsse2enable"></a>_set_SSE2_enable
Habilita o deshabilita el uso de las instrucciones [Extensiones SIMD de streaming 2](http://msdn.microsoft.com/en-us/f98440eb-73a9-4f96-b203-ac41bb6701ea) (SSE2) en las rutinas matemáticas de CRT (esta función no está disponible en las arquitecturas x64 porque SSE2 está habilitada de forma predeterminada).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `flag`  
 1 para habilitar la implementación de SSE2 y 0 para deshabilitarla. De forma predeterminada, la implementación de SSE2 está habilitada en los procesadores compatibles.  
  
## <a name="return-value"></a>Valor devuelto  
 Valor distinto de cero si la implementación de SSE2 está habilitada; cero si está deshabilitada.  
  
## <a name="remarks"></a>Comentarios  
 Las siguientes funciones tienen las implementaciones de SSE2 que se pueden habilitar mediante `_set_SSE2_enable`:  
  
-   [atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [log](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [log10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 Las implementaciones de SSE2 de estas funciones pueden proporcionar respuestas algo diferentes que las implementaciones predeterminadas, porque los valores intermedios de SSE2 son cantidades de punto flotante de 64 bits, mientras que los valores intermedios de implementación predeterminados son cantidades de punto flotante de 80 bits.  
  
> [!NOTE]
>  Si usa la opción del compilador[/Oi (Generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md) para compilar el proyecto, podría parecer que `_set_SSE2_enable` no surte efecto alguno. La opción del compilador `/Oi` da al compilador la autoridad para usar funciones intrínsecas para reemplazar las llamadas de CRT; este comportamiento invalida el efecto de `_set_SSE2_enable`. Si desea garantizar que `/Oi` no invalide `_set_SSE2_enable`, use `/Oi-` para compilar el proyecto. También se recomienda hacer esto si usa otros modificadores de compilador que impliquen `/Oi`.  
  
 La implementación de SSE2 solo se usa si se enmascaran todas las excepciones. Use [_control87, _controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) para enmascarar las excepciones.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_SSE2_enable`|\<math.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_set_SSE2_enable.c  
// processor: x86  
#include <math.h>  
#include <stdio.h>  
  
int main()  
{  
   int i = _set_SSE2_enable(1);  
  
   if (i)  
      printf("SSE2 enabled.\n");  
   else  
      printf("SSE2 not enabled; processor does not support SSE2.\n");  
}  
```  
  
 **Salida**  
  
 `SSE2 enabled.`  
  
## <a name="see-also"></a>Vea también  
 [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md)
