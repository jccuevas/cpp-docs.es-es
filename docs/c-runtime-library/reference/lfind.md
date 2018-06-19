---
title: _lfind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind
- _lfind
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c3bfc7b6abe5f0d5902a02c88e7d5ba16cb24ab
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450655"
---
# <a name="lfind"></a>_lfind

Realiza una búsqueda lineal de la clave especificada. Existe una versión más segura disponible de esta función; vea [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de los datos de búsqueda.

*Número*<br/>
Número de elementos de la matriz.

*width*<br/>
Ancho de los elementos de la matriz.

*compare*<br/>
Puntero a la rutina de comparación. El primer parámetro es un puntero a la clave de búsqueda. El segundo parámetro es un puntero al elemento de la matriz que se va a comparar con la clave.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la clave, **_lfind** devuelve un puntero al elemento de la matriz en *base* que coincida con *clave*. Si no se encuentra la clave, **_lfind** devuelve **NULL**.

## <a name="remarks"></a>Comentarios

El **_lfind** función realiza una búsqueda lineal para el valor *clave* en una matriz de *número* elementos, cada uno de los *ancho* bytes. A diferencia de **bsearch**, **_lfind** no requiere que la matriz se ordenen. El *base* argumento es un puntero a la base de la matriz que se debe buscar. El *comparar* argumento es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y, a continuación, devuelve un valor que especifica la relación. **_lfind** llamadas el *comparar* rutinas una o varias veces durante la búsqueda, pasar punteros a dos elementos de la matriz en cada llamada. El *comparar* rutina debe comparar los elementos y, a continuación, devolver es distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).

Esta función valida sus parámetros. Si *comparar*, *clave* o *número* es **NULL**, o si *base* es **NULL**y *número* es distinto de cero, o si *ancho* es menor que cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
