---
title: _fcvt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: _fcvt
dev_langs: C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c66666d615dc94f74f17736de6011ec05f1eeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fcvt"></a>_fcvt
Convierte un número de punto flotante en una cadena. Existe una versión más segura disponible de esta función; consulte [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_fcvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `count`  
 Número de dígitos después del separador decimal.  
  
 `dec`  
 Puntero a la posición del separador decimal almacenada.  
  
 `sign`  
 Puntero al indicador de signo almacenado.  
  
## <a name="return-value"></a>Valor devuelto  
 `_fcvt` devuelve un puntero a la cadena de dígitos; NULL en caso de error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_fcvt` convierte un número de punto flotante en una cadena de caracteres finalizada en null. El parámetro `value` es el número de punto flotante que se va a convertir. `_fcvt` almacena los dígitos de `value` como cadena y anexa un carácter nulo ("\0"). El parámetro `count` especifica el número de dígitos que se almacenarán después del separador decimal. Los dígitos en exceso se redondean a `count` decimales. Si hay menos de `count` dígitos de precisión, la cadena se rellena con ceros.  
  
 El número total de dígitos que `_fcvt` devuelve no puede superar `_CVTBUFSIZE`.  
  
 Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de `value` pueden obtenerse de `dec` y el signo después de la llamada. El parámetro `dec` apunta a un valor entero; este valor entero proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro `sign` apunta a un entero que indica el signo de `value`. El entero se establece en 0 si `value` es positivo y se establece en un número distinto de cero si `value` es negativo.  
  
 La diferencia entre `_ecvt` y `_fcvt` radica en la interpretación del parámetro `count`. `_ecvt` interpreta `count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt` interpreta `count` como el número de dígitos después del separador decimal.  
  
 `_ecvt` y `_fcvt` usan un solo búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.  
  
 Esta función valida sus parámetros. Si `dec` o `sign` es NULL o `count` es 0, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve NULL.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fcvt`|\<stdlib.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)