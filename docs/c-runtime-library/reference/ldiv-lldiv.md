---
title: ldiv, lldiv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ldiv
- lldiv
dev_langs:
- C++
helpviewer_keywords:
- ldiv function
- lldiv function
- quotients, computing
- computing remainders
- remainder computing
- computing quotients
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cdd241eca666570a47e1ce3ceb74730c6fe35de7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ldiv-lldiv"></a>ldiv, lldiv
Calcula el cociente y el resto de dos enteros como una operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
## <a name="return-value"></a>Valor devuelto  
 `ldiv` devuelve una estructura de tipo [ldiv_t](../../c-runtime-library/standard-types.md) formada por el cociente y el resto. `lldiv` devuelve una estructura de tipo [lldiv_t](../../c-runtime-library/standard-types.md) formada por el cociente y el resto.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `ldiv` y `lldiv` dividen `numer` por `denom` y, por tanto, calculan el cociente y el resto. El signo del cociente es el mismo que el del cociente matemático. El valor absoluto del cociente es el entero más grande que es menor que el valor absoluto del cociente matemático. Si el denominador es 0, el programa se cierra con un mensaje de error. `ldiv` y `lldiv` son iguales que `div`, salvo que los argumentos de `ldiv` y los miembros de la estructura devuelta son todos del tipo `long`, y los argumentos de `lldiv` y los miembros de la estructura devuelta son del tipo `long long`.  
  
 Las estructuras `ldiv_t` y `lldiv_t` se definen en \<stdlib.h.>.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`ldiv`, `lldiv`|\<stdlib.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)