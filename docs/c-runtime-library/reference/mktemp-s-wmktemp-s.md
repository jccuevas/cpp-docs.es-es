---
title: _mktemp_s, _wmktemp_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mktemp_s
- _wmktemp_s
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ed525f44150943496cddde57699035d8b62b6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405229"
---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s

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
Tamaño del búfer en caracteres de byte único en **_mktemp_s**; amplia caracteres de **_wmktemp_s**, incluido el terminador null.

## <a name="return-value"></a>Valor devuelto

Ambas funciones devuelven cero si se realizan correctamente o un código de error en caso de error.

### <a name="error-conditions"></a>Condiciones de error

|*nameTemplate*|*sizeInChars*|Valor devuelto|Nuevo valor en *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|any|**EINVAL**|**NULL**|
|Formato incorrecto (vea la sección Comentarios sección para el formato correcto)|any|**EINVAL**|cadena vacía|
|any|<= número de X|**EINVAL**|cadena vacía|

Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y las funciones devuelven **EINVAL**.

## <a name="remarks"></a>Comentarios

El **_mktemp_s** función crea un nombre de archivo único mediante la modificación de la *nameTemplate* argumento, por lo que después de la llamada, el *nameTemplate* puntero apunta a una cadena que contiene el nuevo nombre de archivo. **_mktemp_s** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso por el sistema en tiempo de ejecución. **_wmktemp_s** es una versión con caracteres anchos de **_mktemp_s**; el argumento de **_wmktemp_s** es una cadena de caracteres anchos. **_wmktemp_s** y **_mktemp_s** se comportan exactamente igual, salvo que **_wmktemp_s** no controla las cadenas de caracteres multibyte.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

El *nameTemplate* argumento tiene la forma **baseXXXXXX**, donde *base* es la parte del nombre de archivo nuevo que suministre y cada X es un marcador de posición de un carácter proporcionado por **_mktemp_s**. Cada carácter marcador de posición de *nameTemplate* debe ser una x en mayúsculas **_mktemp_s** conserva *base* y reemplaza la primera X final con un carácter alfabético. **_mktemp_s** reemplaza los modificadores siguientes x con un valor de cinco dígitos; este valor es un número único que identifica la llamada a proceso, o en los programas multiproceso, el subproceso que realiza la llamada.

Cada llamada correcta a **_mktemp_s** modifica *nameTemplate*. En cada llamada posterior desde el mismo proceso o subproceso con el mismo *nameTemplate* argumento, **_mktemp_s** busca nombres de archivo que coinciden con los nombres devueltos por **_mktemp_s** en las llamadas anteriores. Si no existe ningún archivo para un nombre determinado, **_mktemp_s** devuelve ese nombre. Si existen archivos de todos los previamente devuelven nombres, **_mktemp_s** crea un nuevo nombre si se reemplaza el carácter alfabético que utiliza en el nombre devuelto anteriormente con la siguiente letra minúscula disponible, en orden, de 'a' a la 'z'. Por ejemplo, si *base* es:

> **fn**

y el valor de cinco dígitos proporcionado por **_mktemp_s** es 12345, el nombre devuelto es:

> **fna12345**

Si este nombre se utiliza para crear el archivo FNA12345 y el archivo todavía existe, devuelve el nombre siguiente en una llamada desde el mismo proceso o subproceso con el mismo *base* para *nameTemplate* es:

> **fnb12345**

Si FNA12345 no existe, el siguiente nombre devuelto vuelve a ser:

> **fna12345**

**_mktemp_s** puede crear un máximo de 26 nombres de archivo únicos para cualquier combinación de *base* y *nameTemplate* valores. Por lo tanto, FNZ12345 es el último nombre de archivo único **_mktemp_s** puede crear para la *base* y *nameTemplate* valores utilizados en este ejemplo.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

### <a name="sample-output"></a>Resultados del ejemplo

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
