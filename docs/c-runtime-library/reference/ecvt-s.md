---
title: _ecvt_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs:
- C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 536f9f70547727f2a7a0a4231b1031a67203b1e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ecvts"></a>_ecvt_s
Convierte un número `double` en una cadena. Se trata de una versión de [_ecvt](../../c-runtime-library/reference/ecvt.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `_Buffer`  
 Relleno con el puntero a la cadena de dígitos, el resultado de la conversión.  
  
 [in] `_SizeInBytes`  
 Tamaño del búfer en bytes.  
  
 [in] `_Value`  
 Número que se va a convertir.  
  
 [in] `_Count`  
 Número de dígitos almacenados.  
  
 [out] `_Dec`  
 Posición del separador decimal almacenada.  
  
 [out] `_Sign`  
 Signo del número que se convierte.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 En el caso de un parámetro no válido, como se muestra en la siguiente tabla, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`_Buffer`|`_SizeInBytes`|_Value|_Count|_Dec|_Sign|Valor devuelto|Valor de `buffer`|  
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|No modificado.|  
|No `NULL` (apunta a la memoria válida)|<=0|any|any|any|any|`EINVAL`|No se ha modificado.|  
|any|any|any|any|`NULL`|any|`EINVAL`|No se ha modificado.|  
|any|any|any|any|any|`NULL`|`EINVAL`|No modificado.|  
  
 **Problemas de seguridad**  
  
 Puede que `_ecvt_s` genere una infracción de acceso si `buffer` no apunta a una memoria válida y no es `NULL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_ecvt_s` convierte un número de punto flotante en una cadena de caracteres. El parámetro `_Value` es el número de punto flotante que se va a convertir. Esta función almacena hasta `count` dígitos de `_Value` como cadena y anexa un carácter nulo ("\0"). Si el número de dígitos de `_Value` supera `_Count`, se redondea el dígito de orden inferior. Si hay menos de `count` dígitos, la cadena se rellena con ceros.  
  
 Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de `_Value` pueden obtenerse de `_Dec` y `_Sign` después de la llamada. El parámetro `_Dec` apunta a un valor entero que proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro `_Sign` apunta a un entero que indica el signo del número que se convierte. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.  
  
 Un búfer de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  
  
 La diferencia entre `_ecvt_s` y `_fcvt_s` radica en la interpretación del parámetro `_Count`. `_ecvt_s` interpreta `_Count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt_s` interpreta `_Count` como el número de dígitos después del separador decimal.  
  
 En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 La versión de depuración de esta función rellena primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|--------------|---------------------|---------------------|  
|`_ecvt_s`|\<stdlib.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 12000  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)