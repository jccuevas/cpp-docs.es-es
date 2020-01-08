---
title: gets, _getws
ms.date: 11/04/2016
api_name:
- _getws
- gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: f4e052f91dd2b4adfd5fd7e1ad7c81e0e5b07a11
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300279"
---
# <a name="gets-_getws"></a>gets, _getws

Obtiene una línea del flujo `stdin` . Hay disponibles versiones más seguras de estas funciones; vea [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT. Las versiones seguras de estas funciones, gets_s y _getws_s, siguen estando disponibles. Para obtener información sobre estas funciones alternativas, vea [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Parameters

*buffer*<br/>
Ubicación de almacenamiento de la cadena de entrada.

## <a name="return-value"></a>Valor devuelto

Devuelve su argumento si se realiza correctamente. Un puntero **NULL** indica una condición de error o de fin de archivo. Utilice [ferror](../c-runtime-library/reference/ferror.md) o [feof](../c-runtime-library/reference/feof.md) para determinar qué resultado se ha producido. Si `buffer` es **NULL**, estas funciones invocan un controlador de parámetros no válido, tal y como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Si se permite que la ejecución continúe, estas funciones devuelven **NULL** y establecen errno en `EINVAL`.

## <a name="remarks"></a>Notas

La función `gets` lee una línea del flujo de entrada estándar `stdin` y la almacena en `buffer`. La línea consta de todos los caracteres hasta el primer carácter de línea nueva ('\n'), este último incluido. A continuación,`gets` reemplaza el carácter de línea nueva con un carácter nulo ('\0') antes de devolver la línea. Por su parte, la función `fgets` conserva el carácter de línea nueva. `_getws` es una versión con caracteres anchos de `gets`; el argumento y el valor devuelto son cadenas de caracteres anchos.

> [!IMPORTANT]
>  No hay forma de limitar el número de caracteres que gets lee, por lo que una entrada que no sea de confianza puede producir fácilmente saturaciones del búfer. Utilice `fgets` en su lugar.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

Observe que una entrada de más 20 caracteres saturará el búfer de líneas y provocará casi con seguridad que el programa se bloquee.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
