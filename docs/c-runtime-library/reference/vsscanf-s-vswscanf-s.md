---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: bacda4288a6745ea57c31e68e515ae7b37418096
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946015"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s, vswscanf_s

Lee datos con formato de una cadena. Estas versiones de [vsscanf, vswscanf](vsscanf-vswscanf.md) tienen mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Datos almacenados

*format*<br/>
Cadena de control de formato. Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Lista de argumentos de variable.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error o si el final de la cadena se alcanza antes de la primera conversión.

Si *buffer* o *Format* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 y establecen **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **vsscanf_s** Lee los datos del *búfer* en las ubicaciones especificadas por cada argumento en la lista de argumentos *arglist* . Los argumentos de la lista de argumentos especifican punteros a variables que tienen un tipo que se corresponde con un especificador de tipo en *formato*. A diferencia de la versión menos segura **vsscanf**, se requiere un parámetro de tamaño de búfer cuando se usan los caracteres de campo de tipo **c**, **c**, **s**, **s**o los conjuntos de control de cadena que se incluyen en **[]** . El tamaño de búfer en caracteres se debe proporcionar como un parámetro adicional inmediatamente después de cada parámetro de búfer que lo necesite.

El tamaño de búfer incluye el valor nulo final. Se puede usar un campo de especificación del ancho para garantizar que el token se ajustará al búfer. Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.

Para obtener más información, vea [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) y [scanf (Caracteres de campo de tipo)](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> El parámetro de tamaño es de tipo sin **signo**, no **size_t**.

El argumento de *formato* controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento de *formato* para la función **scanf_s** . Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

**vswscanf_s** es una versión con caracteres anchos de **vsscanf_s**; los argumentos de **vswscanf_s** son cadenas de caracteres anchos. **vsscanf_s** no controla caracteres hexadecimales multibyte. **vswscanf_s** no controla los caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode. De lo contrario, **vswscanf_s** y **vsscanf_s** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
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
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
