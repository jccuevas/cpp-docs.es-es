---
title: gets_s, _getws_s
ms.date: 4/2/2020
api_name:
- _getws_s
- gets_s
- _o__getws_s
- _o_gets_s
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
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: aac64a42a2979623f4314f7bf28d7e4917eaee18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344218"
---
# <a name="gets_s-_getws_s"></a>gets_s, _getws_s

Obtiene una línea de la corriente **de stdin.** Estas versiones de [gets, _getws](../../c-runtime-library/gets-getws.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Ubicación de almacenamiento de la cadena de entrada.

*sizeInCharacters*<br/>
Tamaño del búfer.

## <a name="return-value"></a>Valor devuelto

Devuelve *el búfer* si se realiza correctamente. Un puntero **NULL** indica una condición de error o de fin de archivo. Utilice [ferror](ferror.md) o [feof](feof.md) para determinar qué resultado se ha producido.

## <a name="remarks"></a>Observaciones

La función **gets_s** lee una línea del **stdin** de flujo de entrada estándar y la almacena en *búfer.* La línea consta de todos los caracteres hasta el primer carácter de línea nueva ('\n'), este último incluido. **gets_s,** a continuación, reemplaza el carácter de nueva línea con un carácter nulo ('-0') antes de devolver la línea. Por el contrario, la función **fgets_s** conserva el carácter de nueva línea.

Si la primera lectura de caracteres es el carácter de fin de archivo, se almacena un carácter nulo al principio del *búfer* y se devuelve **NULL.**

**_getws_s** es una versión de caracteres anchos de **gets_s;** su argumento y valor devuelto son cadenas de caracteres anchos.

Si *buffer* es **NULL** o *sizeInCharacters* es menor o igual que cero, o si el búfer es demasiado pequeño para contener la línea de entrada y el terminador nulo, estas funciones invocan un controlador de parámetros no válido, como se describe en [Validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si la ejecución puede continuar, estas funciones devuelven **NULL** y establecen errno en **ERANGE**.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola, **stdin,** **stdout**y **stderr**, deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[obtiene, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
