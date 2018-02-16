---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
dev_langs:
- C++
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791f9b7408fded070fe61206d4303c26c8926d3e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s
Obtiene un mensaje de error del sistema (`strerror_s`, `_wcserror_s`), o imprime un mensaje de error proporcionado por el usuario (`_strerror_s`, `__wcserror_s`). Se trata de versiones de [strerror, _strerror, _wcserror, \__wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Búfer que va a contener la cadena de error.  
  
 `numberOfElements`  
 Tamaño del búfer.  
  
 `errnum`  
 Número de error.  
  
 `strErrMsg`  
 Mensaje proporcionado por el usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### <a name="error-condtions"></a>Condiciones de error  
  
|`buffer`|`numberOfElements`|`strErrMsg`|Contenido de `buffer`|  
|--------------|------------------------|-----------------|--------------------------|  
|`NULL`|any|any|N/D|  
|any|0|any|no modificado|  
  
## <a name="remarks"></a>Comentarios  
 La función `strerror_s` asigna `errnum` a una cadena de mensaje de error, y devuelve la cadena de `buffer`. `_strerror_s` no toma el número de error. Usa el valor actual de `errno` para determinar el mensaje adecuado. Ni `strerror_s` ni `_strerror_s` imprimen realmente el mensaje. Para hacerlo, se debe llamar a una función de salida, como [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 Si `strErrMsg` es `NULL`, `_strerror_s` devuelve una cadena en `buffer` que contiene el mensaje de error del sistema de la última llamada a biblioteca que generó un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Si `strErrMsg` no es igual a `NULL`, `_strerror_s` devuelve una cadena en `buffer` que contiene (en orden) el mensaje de cadena, dos puntos, un espacio, el mensaje de error del sistema de la última llamada a biblioteca que generó un error, y un carácter de línea nueva. El mensaje de cadena puede tener, como máximo, 94 caracteres.  
  
 Estas funciones truncan el mensaje de error si su longitud supera `numberOfElements` -1. La cadena resultante en `buffer` siempre termina con un valor NULL.  
  
 El número de error real de `_strerror_s` se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Se obtiene acceso a los mensajes de error del sistema a través de la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error. `_strerror_s` obtiene acceso al mensaje de error adecuado mediante el valor de `errno` como índice de la variable `_sys_errlist`. El valor de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz `_sys_errlist`. Para generar resultados precisos, llame a `_strerror_s` inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas subsiguientes a `strerror_s` o `_strerror_s` pueden sobrescribir el valor de `errno`.  
  
 `_wcserror_s` y `__wcserror_s` son versiones con caracteres anchos de `strerror_s` y `_strerror_s`, respectivamente.  
  
 Estas funciones validan sus parámetros. Si el búfer es `NULL` o si el parámetro de tamaño es 0, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
 `_strerror_s`, `_wcserror_s`, y `__wcserror_s` no forman parte de la definición de ANSI, pero en su lugar, son extensiones de Microsoft a él. No se deben usar si se desea disponer de portabilidad. Para obtener compatibilidad con ANSI, use `strerror_s`.  
  
 En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`strerror_s`, `_strerror_s`|\<string.h>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [perror](../../c-runtime-library/reference/perror-wperror.md).  
  
## <a name="see-also"></a>Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)