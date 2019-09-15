---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
api_name:
- _wmktemp
- _mktemp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: 7cfca04d4f0df2673a2221f00a1263f73e8516ec
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951577"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

Crea un nombre de archivo único. Hay disponibles versiones más seguras de estas funciones; vea [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*nameTemplate*<br/>
Patrón de nombre de archivo.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al nameTemplate modificado. La función devuelve **null** si *nameTemplate* tiene un formato incorrecto o no se pueden crear más nombres únicos a partir de la nameTemplate especificada.

## <a name="remarks"></a>Comentarios

La función **_mktemp** crea un nombre de archivo único modificando el argumento *nameTemplate* . **_mktemp** controla automáticamente los argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso por el sistema en tiempo de ejecución. **_wmktemp** es una versión con caracteres anchos de **_mktemp**; el argumento y el valor devuelto de **_wmktemp** son cadenas de caracteres anchos. **_wmktemp** y **_mktemp** se comportan de manera idéntica, salvo que **_wmktemp** no controla las cadenas de caracteres multibyte.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

El argumento *nameTemplate* tiene el formato *base*xxxxxx, donde *base* es la parte del nuevo nombre de archivo que se proporciona y cada X es un marcador de posición para un carácter proporcionado por **_mktemp**. Cada carácter de marcador de posición de *nameTemplate* debe ser una x mayúscula. **_mktemp** conserva la *base* y reemplaza la primera x final por un carácter alfabético. **_mktemp** reemplaza los siguientes X finales por un valor de cinco dígitos; Este valor es un número único que identifica el proceso de llamada o, en programas multiproceso, el subproceso que realiza la llamada.

Cada llamada correcta a **_mktemp** modifica *nameTemplate*. En cada llamada subsiguiente del mismo proceso o subproceso con el mismo argumento *nameTemplate* , **_mktemp** comprueba si hay nombres de archivo que coincidan con los nombres devueltos por **_mktemp** en llamadas anteriores. Si no existe ningún archivo para un nombre dado, **_mktemp** devuelve ese nombre. Si existen archivos para todos los nombres devueltos anteriormente, **_mktemp** crea un nuevo nombre reemplazando el carácter alfabético que se usa en el nombre devuelto anteriormente por la siguiente letra minúscula disponible, en orden, de la "a" a la "z". Por ejemplo, si *base* es:

> **fn**

y el valor de cinco dígitos proporcionado por **_mktemp** es 12345, el primer nombre devuelto es:

> **fna12345**

Si este nombre se usa para crear el archivo FNA12345 y este archivo todavía existe, el siguiente nombre devuelto en una llamada del mismo proceso o subproceso con la misma *base* para *nameTemplate* es:

> **fnb12345**

Si FNA12345 no existe, el siguiente nombre devuelto vuelve a ser:

> **fna12345**

**_mktemp** puede crear un máximo de 26 nombres de archivo únicos para una combinación determinada de valores *base* y *nameTemplate* . Por lo tanto, FNZ12345 es el último nombre de archivo único que **_mktemp** puede crear para los valores *base* y *nameTemplate* que se usan en este ejemplo.

En caso de error, **errno** está establecido. Si *nameTemplate* tiene un formato no válido (por ejemplo, menos de 6 X), **errno** se establece en **EINVAL**. Si **_mktemp** no puede crear un nombre único porque ya existen los 26 nombres de archivo posibles, **_mktemp** establece nameTemplate en una cadena vacía y devuelve **EEXIST**.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
