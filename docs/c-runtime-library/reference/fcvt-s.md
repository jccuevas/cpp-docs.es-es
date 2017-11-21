---
title: _fcvt_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt_s
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
- fcvt_s
- _fcvt_s
dev_langs: C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 922fed9dde6e3f38ae1276034ce84a97db9f99be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fcvts"></a>_fcvt_s
Convierte un número de punto flotante en una cadena. Se trata de una versión de [_fcvt](../../c-runtime-library/reference/fcvt.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `buffer`  
 Búfer proporcionado que contendrá el resultado de la conversión.  
  
 [in] `sizeInBytes`  
 Tamaño del búfer en bytes.  
  
 [in] `value`  
 Número que se va a convertir.  
  
 [in] `count`  
 Número de dígitos después del separador decimal.  
  
 [out] `dec`  
 Puntero a la posición del separador decimal almacenada.  
  
 [out] `sign`  
 Puntero al indicador de signo almacenado.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 En el caso de un parámetro no válido, como se muestra en la siguiente tabla, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`buffer`|`sizeInBytes`|valor|count|dec|sign|Valor devuelto|Valor de `buffer`|  
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|  
|`NULL`|cualquiera|cualquiera|cualquiera|cualquiera|cualquiera|`EINVAL`|No modificado.|  
|No `NULL` (apunta a la memoria válida)|<=0|any|cualquiera|cualquiera|cualquiera|`EINVAL`|No se ha modificado.|  
|any|cualquiera|cualquiera|cualquiera|`NULL`|cualquiera|`EINVAL`|No se ha modificado.|  
|any|cualquiera|cualquiera|cualquiera|cualquiera|`NULL`|`EINVAL`|No se ha modificado.|  
  
 **Problemas de seguridad**  
  
 Puede que `_fcvt_s` genere una infracción de acceso si `buffer` no apunta a una memoria válida y no es `NULL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_fcvt_s` convierte un número de punto flotante en una cadena de caracteres finalizada en null. El parámetro `value` es el número de punto flotante que se va a convertir. `_fcvt_s` almacena los dígitos de `value` como cadena y anexa un carácter nulo ("\0"). El parámetro `count` especifica el número de dígitos que se almacenarán después del separador decimal. Los dígitos en exceso se redondean a `count` decimales. Si hay menos de `count` dígitos de precisión, la cadena se rellena con ceros.  
  
 Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de `value` pueden obtenerse de `dec` y `sign` después de la llamada. El parámetro `dec` apunta a un valor entero; este valor entero proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro `sign` apunta a un entero que indica el signo de `value`. El entero se establece en 0 si `value` es positivo y se establece en un número distinto de cero si `value` es negativo.  
  
 Un búfer de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  
  
 La diferencia entre `_ecvt_s` y `_fcvt_s` radica en la interpretación del parámetro `count`. `_ecvt_s`interpreta `count` como el número total de dígitos en la cadena de salida, y `_fcvt_s` interpreta `count` como el número de dígitos después del separador decimal.  
  
 En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulte [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 La versión de depuración de esta función rellena primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|--------------|---------------------|---------------------|  
|`_fcvt_s`|\<stdlib.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** todas las versiones de las [características de la biblioteca de CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 120000  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)