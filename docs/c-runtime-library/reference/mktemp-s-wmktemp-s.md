---
title: _mktemp_s, _wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338753"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Crea un nombre de archivo único. Se trata de versiones de [_mktemp, _wmktemp](mktemp-wmktemp.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*nameTemplate*<br/>
Patrón de nombre de archivo.

*sizeInChars*<br/>
Tamaño del búfer en caracteres de un solo byte en **_mktemp_s**; caracteres anchos en **_wmktemp_s,** incluido el terminador nulo.

## <a name="return-value"></a>Valor devuelto

Ambas funciones devuelven cero si se realizan correctamente o un código de error en caso de error.

### <a name="error-conditions"></a>Condiciones de error

|*nameTemplate*|*sizeInChars*|Valor devuelto|Nuevo valor en *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**Null**|cualquiera|**EINVAL**|**Null**|
|Formato incorrecto (consulte la sección Comentarios para el formato correcto)|cualquiera|**EINVAL**|cadena vacía|
|cualquiera|<= número de X|**EINVAL**|cadena vacía|

Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y las funciones devuelven **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_mktemp_s** crea un nombre de archivo único modificando el argumento *nameTemplate,* de modo que después de la llamada, el puntero *nameTemplate* apunte a una cadena que contenga el nuevo nombre de archivo. **_mktemp_s** controla automáticamente los argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso por el sistema en tiempo de ejecución. **_wmktemp_s** es una versión de caracteres anchos de **_mktemp_s;** el argumento de **_wmktemp_s** es una cadena de caracteres anchos. **_wmktemp_s** y **_mktemp_s** se comportan de forma idéntica de lo contrario, excepto que **_wmktemp_s** no controla cadenas de caracteres multibyte.

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

El argumento *nameTemplate* tiene el formulario **baseXXXXXX**, donde *base* es la parte del nuevo nombre de archivo que se proporciona y cada X es un marcador de posición para un carácter proporcionado por **_mktemp_s**. Cada carácter de marcador de posición en *nameTemplate* debe ser una X mayúscula **_mktemp_s** conserva *base* y reemplaza la primera X final con un carácter alfabético. **_mktemp_s** reemplaza las siguientes X finales por un valor de cinco dígitos; este valor es un número único que identifica el proceso de llamada, o en programas multiproceso, el subproceso de llamada.

Cada llamada correcta a **_mktemp_s** modifica *nameTemplate*. En cada llamada posterior desde el mismo proceso o subproceso con el mismo *nameTemplate* argumento, **_mktemp_s** comprueba los nombres de archivo que coinciden con los nombres devueltos por **_mktemp_s** en llamadas anteriores. Si no existe ningún archivo para un nombre determinado, **_mktemp_s** devuelve ese nombre. Si existen archivos para todos los nombres devueltos anteriormente, **_mktemp_s** crea un nuevo nombre reemplazando el carácter alfabético que utilizó en el nombre devuelto anteriormente por la siguiente letra minúscula disponible, en orden, de 'a' a 'z'. Por ejemplo, si *la base* es:

> **fn**

y el valor de cinco dígitos proporcionado por **_mktemp_s** es 12345, el primer nombre devuelto es:

> **fna12345**

Si este nombre se utiliza para crear el archivo FNA12345 y este archivo todavía existe, el siguiente nombre devuelto en una llamada del mismo proceso o subproceso con la misma *base* para *nameTemplate* es:

> **fnb12345**

Si FNA12345 no existe, el siguiente nombre devuelto vuelve a ser:

> **fna12345**

**_mktemp_s** puede crear un máximo de 26 nombres de archivo únicos para cualquier combinación determinada de valores *base* y *nameTemplate.* Por lo tanto, FNZ12345 es el último nombre de archivo único **que _mktemp_s** puede crear para los valores *base* y *nameTemplate* utilizados en este ejemplo.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
