---
title: _ecvt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ecvt
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
f1_keywords:
- _ecvt
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c3992066b5b305a7b9de6ef47c6ba42e15da2518
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="ecvt"></a>_ecvt
Convierte un número `double` en una cadena. Existe una versión más segura disponible de esta función; consulte [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_ecvt(   
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
 Número de dígitos almacenados.  
  
 `dec`  
 Posición del separador decimal almacenada.  
  
 `sign`  
 Signo del número que se convierte.  
  
## <a name="return-value"></a>Valor devuelto  
 `_ecvt` devuelve un puntero a la cadena de dígitos; NULL si se ha producido un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_ecvt` convierte un número de punto flotante en una cadena de caracteres. El parámetro `value` es el número de punto flotante que se va a convertir. Esta función almacena hasta `count` dígitos de `value` como cadena y anexa un carácter nulo ("\0"). Si el número de dígitos de `value` supera `count`, se redondea el dígito de orden inferior. Si hay menos de `count` dígitos, la cadena se rellena con ceros.  
  
 El número total de dígitos que `_ecvt` devuelve no puede superar `_CVTBUFSIZE`.  
  
 Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de `value` pueden obtenerse de `dec` y `sign` después de la llamada. El parámetro `dec` apunta a un valor entero que proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro `sign` apunta a un entero que indica el signo del número que se convierte. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.  
  
 La diferencia entre `_ecvt` y `_fcvt` radica en la interpretación del parámetro `count`. `_ecvt` interpreta `count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt` interpreta `count` como el número de dígitos después del separador decimal.  
  
 `_ecvt` y `_fcvt` usan un solo búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.  
  
 Esta función valida sus parámetros. Si `dec` o `sign` es NULL o `count` es 0, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve NULL.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_ecvt`|\<stdlib.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)
