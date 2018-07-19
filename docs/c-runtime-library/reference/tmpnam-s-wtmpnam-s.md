---
title: tmpnam_s, _wtmpnam_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c6298c7b66c8967a4e5e23a37c3614edcddf3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415535"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s

Genere nombres que se puedan usar para crear archivos temporales. Estas son versiones de [tmpnam y _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Puntero que va a contener el nombre generado.

*sizeInChars*<br/>
Tamaño del búfer en caracteres.

## <a name="return-value"></a>Valor devuelto

Ambas funciones devuelven 0 si se realizan correctamente o un número de error en caso contrario.

### <a name="error-conditions"></a>Condiciones de error

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Valor devuelto**|**Contenido de***str* |
|**NULL**|any|**EINVAL**|no modificado|
|No **NULL** (apunta a la memoria válido)|demasiado corto|**ERANGE**|no modificado|

Si *str* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EINVAL**.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones devuelve el nombre de un archivo que no existe en este momento. **tmpnam_s** devuelve un nombre único en el directorio de trabajo actual. Tenga en cuenta que cuando un nombre de archivo va precedido por una barra diagonal inversa sin información de ruta de acceso, como \fname21, esto indica que el nombre es válido para el directorio de trabajo actual.

Para **tmpnam_s**, puede almacenar este nombre de archivo generado en *str*. La longitud máxima de una cadena devuelta por **tmpnam_s** es **L_tmpnam_s**, definido en STDIO. H. Si *str* es **NULL**, a continuación, **tmpnam_s** deja el resultado en un búfer interno estático. Por lo tanto, las siguientes llamadas destruyen este valor. El nombre generado por **tmpnam_s** consta de un nombre de archivo generado por el programa y, después de la primera llamada a **tmpnam_s**, una extensión de archivo de los números secuenciales de 32 base (cuando.1-.1vvvvvu, **TMP _MAX_S** en STDIO. H es **INT_MAX**).

**tmpnam_s** automáticamente argumentos de cadena de caracteres multibyte de identificadores según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos OEM obtienen del sistema operativo. **_wtmpnam_s** es una versión con caracteres anchos de **tmpnam_s**; el argumento y el valor devuelto de **_wtmpnam_s** son cadenas de caracteres anchos. **_wtmpnam_s** y **tmpnam_s** se comportan exactamente igual, salvo que **_wtmpnam_s** no controla las cadenas de caracteres multibyte.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulte [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
