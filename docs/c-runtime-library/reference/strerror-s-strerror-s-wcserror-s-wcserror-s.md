---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 06/09/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
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
ms.openlocfilehash: 91be8803a0695670e7afe673b25b54fccde40a9c
ms.sourcegitcommit: 8167c67d76de58a7c2df3b4dcbf3d53e3b151b77
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2020
ms.locfileid: "84664331"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Obtiene un mensaje de error del sistema (**strerror_s**, **_wcserror_s**) o imprime un mensaje de error proporcionado por el usuario (**_strerror_s**, **__wcserror_s**). Se trata de versiones de [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t strerror_s(
   char *buffer,
   size_t sizeInBytes,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t sizeInBytes,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
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

### <a name="parameters"></a>Parámetros

*búfer*<br/>
Búfer que va a contener la cadena de error.

*sizeInBytes*<br/>
El número de bytes en el búfer.

*sizeInWords*<br/>
Número de palabras en el búfer.

*elementos errnum*<br/>
Número de error.

*strErrMsg*<br/>
Mensaje proporcionado por el usuario.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-condtions"></a>Condiciones de error

|*búfer*|*sizeInBytes/sizeInWords*|*strErrMsg*|Contenido del *búfer*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|cualquiera|cualquiera|N/D|
|cualquiera|0|cualquiera|no modificado|

## <a name="remarks"></a>Observaciones

La función **strerror_s** asigna *elementos errnum* a una cadena de mensaje de error y devuelve la cadena en el *búfer*. **_strerror_s** no toma el número de error; utiliza el valor actual de **errno** para determinar el mensaje adecuado. Ni **strerror_s** ni **_strerror_s** realmente imprimen el mensaje: para ello, debe llamar a una función de salida como [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Si *strErrMsg* es **null**, **_strerror_s** devuelve una cadena en el *búfer* que contiene el mensaje de error del sistema para la última llamada de biblioteca que generó un error. La cadena del mensaje de error termina con el carácter de línea nueva ('\n'). Si *strErrMsg* no es igual a **null**, **_strerror_s** devuelve una cadena en el *búfer* que contiene (en orden) el mensaje de cadena, un signo de dos puntos, un espacio, el mensaje de error del sistema para la última llamada de biblioteca que produce un error y un carácter de nueva línea. El mensaje de cadena puede tener, como máximo, 94 caracteres.

Estas funciones truncan el mensaje de error si su longitud supera el tamaño del búfer-1. La cadena resultante en el *búfer* siempre terminará en NULL.

El número de error real de **_strerror_s** se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Se obtiene acceso a los mensajes de error del sistema a través de la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error. **_strerror_s** tiene acceso al mensaje de error adecuado mediante el valor **errno** como un índice para la variable **_sys_errlist**. El valor de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz de **_sys_errlist** . Para generar resultados precisos, llame a **_strerror_s** inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas subsiguientes a **strerror_s** o **_strerror_s** pueden sobrescribir el valor **errno** .

**_wcserror_s** y **__wcserror_s** son versiones con caracteres anchos de **strerror_s** y **_strerror_s**, respectivamente.

Estas funciones validan sus parámetros. Si buffer es **null** o el parámetro size es 0, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, las funciones devuelven **EINVAL** y establecen **errno** en **EINVAL**.

**_strerror_s**, **_wcserror_s**y **__wcserror_s** no forman parte de la definición ANSI, sino que son extensiones de Microsoft. No las use si desea portabilidad; para la compatibilidad con ANSI, use **strerror_s** en su lugar.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s**, **__wcserror_s**|\<string.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [perror](perror-wperror.md).

## <a name="see-also"></a>Consulte también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
