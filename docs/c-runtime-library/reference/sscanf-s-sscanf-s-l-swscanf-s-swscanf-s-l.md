---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 14707b64a9c5c49837391be59d83ee39b79d5065
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957967"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Lee datos con formato de una cadena. Estas versiones de [sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Datos almacenados

*format*<br/>
Cadena de control de formato. Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Argumentos opcionales

*locale*<br/>
Configuración regional que se va a usar

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error o si el final de la cadena se alcanza antes de la primera conversión.

Si *buffer* o *Format* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en **EINVAL**

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **sscanf_s** Lee los datos del *búfer* en la ubicación especificada por cada *argumento*. Los argumentos después de la cadena de formato especifican punteros a variables que tienen un tipo que se corresponde con un especificador de tipo en *formato*. A diferencia de la versión menos segura [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md), se requiere un parámetro de tamaño de búfer cuando se usan los caracteres de campo de tipo **c**, **c**, **s**, **s**o los conjuntos de control de cadenas que se incluyen en **[]** . El tamaño de búfer en caracteres se debe proporcionar como un parámetro adicional inmediatamente después de cada parámetro de búfer que lo necesite. Por ejemplo, si está leyendo en una cadena, el tamaño de búfer para esa cadena se pasa como se indica a continuación:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

El tamaño de búfer incluye el valor nulo final. Se puede usar un campo de especificación del ancho para garantizar que el token se ajustará al búfer. Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.

En el caso de los caracteres, un carácter individual puede leerse como se indica a continuación:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

En este ejemplo se lee un solo carácter de la cadena de entrada y se almacena en un búfer de caracteres anchos. Al leer varios caracteres para cadenas que no tienen un valor nulo final, se usan enteros sin signo como especificación del ancho y el tamaño de búfer.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Para obtener más información, vea [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) y [scanf (Caracteres de campo de tipo)](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> El parámetro de tamaño es de tipo sin **signo**, no **size_t**. Al compilar para destinos de 64 bits, utilice una conversión estática para convertir los resultados de **_countof** o **sizeof** al tamaño correcto.

El argumento de *formato* controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento de *formato* para la función **scanf_s** . Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

**swscanf_s** es una versión con caracteres anchos de **sscanf_s**; los argumentos de **swscanf_s** son cadenas de caracteres anchos. **sscanf_s** no controla caracteres hexadecimales multibyte. **swscanf_s** no controla los caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode. De lo contrario, **swscanf_s** y **sscanf_s** se comportan exactamente igual.

Las versiones de estas funciones que tienen el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
