---
title: _tempnam, _wtempnam, tmpnam, _wtmpnam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55ff069d72d68493eee524ea2f9c012d2fc7f534
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417018"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Genere nombres que se puedan usar para crear archivos temporales. Hay disponibles versiones más seguras de algunas de estas funciones; vea [tmpnam_s, _wtmpnam_s](tmpnam-s-wtmpnam-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>Parámetros

*Prefijo*<br/>
La cadena que se va a anteponer a nombres devueltos por **_tempnam**.

*dir*<br/>
Ruta de acceso que se usa en el nombre de archivo si no hay variable de entorno TMP, o si TMP no es un directorio válido.

*str*<br/>
Puntero que va a conservar el nombre generado, que será idéntico al nombre devuelto por la función. Se trata de una manera cómoda de guardar el nombre generado.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al nombre generado o **NULL** si se produce un error. Error puede ocurrir si se intenta superar **TMP_MAX** (vea STDIO. (H) llamadas con **tmpnam** o si utiliza **_tempnam** y no hay un nombre de directorio no válido especificado en la variable de entorno TMP y en el *dir* parámetro.

> [!NOTE]
> Los punteros devueltos por **tmpnam** y **_wtmpnam** seleccione búferes estáticos internos. No debe llamarse a [free](free.md) para desasignar esos punteros. **libre** debe llamarse para punteros asignados por **_tempnam** y **_wtempnam**.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones devuelve el nombre de un archivo que no existe en este momento. **tmpnam** devuelve un nombre único en el directorio de trabajo actual y **_tempnam** permite generar un nombre único en un directorio distinto del actual. Tenga en cuenta que cuando un nombre de archivo va precedido por una barra diagonal inversa sin información de ruta de acceso, como \fname21, esto indica que el nombre es válido para el directorio de trabajo actual.

Para **tmpnam**, puede almacenar este nombre de archivo generado en *str*. Si *str* es **NULL**, a continuación, **tmpnam** deja el resultado en un búfer interno estático. Por lo tanto, las siguientes llamadas destruyen este valor. El nombre generado por **tmpnam** consta de un nombre de archivo generado por el programa y, después de la primera llamada a **tmpnam**, una extensión de archivo de los números secuenciales de 32 base (cuando.1-.vvu, **TMP_MAX**  en STDIO. H es de 32.767).

**_tempnam** generará un nombre de archivo único para un directorio elegido por las reglas siguientes:

- Si la variable de entorno TMP está definida y establecida en un nombre de directorio válido, se generarán nombres de archivo únicos para el directorio especificado por TMP.

- Si no se define la variable de entorno TMP, o si se establece en el nombre de un directorio que no existe, **_tempnam** usará la *dir* parámetro como la ruta de acceso para el que va a generar nombres únicos.

- Si no se define la variable de entorno TMP o si se establece en el nombre de un directorio que no existe y si *dir* sea **NULL** o se establece en el nombre de un directorio que no existe, **_ tempnam** utilizará el directorio de trabajo actual para generar nombres únicos. En la actualidad, si ambos TMP y *dir* especificar nombres de los directorios que no existen, el **_tempnam** se producirá un error en la llamada de función.

El nombre devuelto por **_tempnam** será una concatenación de *prefijo* y un número secuencial que se combina para crear un nombre de archivo único para el directorio especificado. **_tempnam** genera nombres de archivo que no tienen ninguna extensión. **_tempnam** utiliza [malloc](malloc.md) para asignar espacio para el nombre de archivo; el programa es responsable de este espacio que libera cuando ya no es necesario.

**_tempnam** y **tmpnam** automáticamente argumentos de cadena de caracteres multibyte de identificador según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos OEM obtienen del sistema operativo. **_wtempnam** es una versión con caracteres anchos de **_tempnam**; los argumentos y el valor devuelto de **_wtempnam** son cadenas de caracteres anchos. **_wtempnam** y **_tempnam** se comportan exactamente igual, salvo que **_wtempnam** no controla las cadenas de caracteres multibyte. **_wtmpnam** es una versión con caracteres anchos de **tmpnam**; el argumento y el valor devuelto de **_wtmpnam** son cadenas de caracteres anchos. **_wtmpnam** y **tmpnam** se comportan exactamente igual, salvo que **_wtmpnam** no controla las cadenas de caracteres multibyte.

Si **_DEBUG** y **_CRTDBG_MAP_ALLOC** se definen, **_tempnam** y **_wtempnam** se reemplazan por llamadas a [_tempnam _dbg y _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**, **_wtmpnam**|\<stdio.h> o \<wchar.h>|
|**tmpnam**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
