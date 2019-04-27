---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
apiname:
- _wmktemp
- _mktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: c1c5f0ee12c9e07d76405014bb4a6a6ecc7d97e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156517"
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

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

Cada una de estas funciones devuelve un puntero a la nametemplate no modificado. La función devuelve **NULL** si *nametemplate no* tiene un formato incorrecto o no hay más nombres únicos pueden crearse desde el nametemplate no determinado.

## <a name="remarks"></a>Comentarios

El **_mktemp** función crea un nombre de archivo único modificando el *nametemplate no* argumento. **_mktemp** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso por el sistema de tiempo de ejecución. **_wmktemp** es una versión con caracteres anchos de **_mktemp**; el argumento y el valor devuelto de **_wmktemp** son cadenas de caracteres anchos. **_wmktemp** y **_mktemp** se comportan exactamente igual, salvo que **_wmktemp** no controla las cadenas de caracteres multibyte.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

El *nametemplate no* argumento tiene el formato *base*XXXXXX, donde *base* es la parte del nuevo nombre de archivo que se proporciona y cada X es un marcador de posición de un carácter proporcionado por **_mktemp**. Cada carácter marcador de posición de *nametemplate no* debe ser una x mayúscula. **_mktemp** conserva *base* y reemplaza la primera X final por un carácter alfabético. **_mktemp** reemplaza los siguientes modificadores x con un valor de cinco dígitos; este valor es un número único que identifica la llamada a proceso, o en programas multiproceso, el subproceso de llamada.

Cada llamada correcta a **_mktemp** modifica *nametemplate no*. En cada llamada posterior realizada desde el mismo proceso o subproceso con el mismo *nametemplate no* argumento, **_mktemp** busca los nombres de archivo que coinciden con los nombres devueltos por **_mktemp** en llamadas anteriores. Si no existe ningún archivo para un determinado nombre **_mktemp** devuelve ese nombre. Si existen archivos de todos los nombres devuelven previamente, **_mktemp** crea un nuevo nombre si se reemplaza el carácter alfabético que emplea en el nombre devuelto anteriormente por la siguiente letra minúscula disponible, en orden, de 'a' a 'z'. Por ejemplo, si *base* es:

> **fn**

y el valor de cinco dígitos proporcionado por **_mktemp** es 12345, el primer nombre devuelto es:

> **fna12345**

Si este nombre se usa para crear el archivo FNA12345 y el archivo todavía existe, el siguiente nombre devuelto en una llamada desde el mismo proceso o subproceso con el mismo *base* para *nametemplate no* es:

> **fnb12345**

Si FNA12345 no existe, el siguiente nombre devuelto vuelve a ser:

> **fna12345**

**_mktemp** puede crear un máximo de 26 nombres de archivo únicos para cualquier combinación de *base* y *nametemplate no* valores. Por lo tanto, FNZ12345 es el último nombre de archivo único **_mktemp** puede crear para el *base* y *nametemplate no* valores utilizados en este ejemplo.

En caso de error, **errno** está establecido. Si *nametemplate no* tiene un formato no válido (por ejemplo, menos de 6 x), **errno** está establecido en **EINVAL**. Si **_mktemp** no puede crear un nombre único porque ya existen todos los 26 nombres de archivo posibles, **_mktemp** nametemplate no se establece en una cadena vacía y devuelve **EEXIST**.

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
