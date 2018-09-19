---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5166ef52f88e714d1168fe25a1ec29dd5360205
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210510"
---
# <a name="vsnprintf-vsnprintf-vsnprintfl-vsnwprintf-vsnwprintfl"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

Escribe un resultado con formato mediante un puntero a una lista de argumentos. Hay disponibles versiones más seguras de estas funciones; vea [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento del resultado.

*count*<br/>
Número máximo de caracteres que se van a escribir.

*format*<br/>
Especificación de formato.

*argptr*<br/>
Puntero a la lista de argumentos.

*locale*<br/>
Configuración regional que se va a usar.

Para más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

El **vsnprintf** función devuelve el número de caracteres escritos, sin contar el carácter nulo de terminación. Si el tamaño de búfer especificado por *recuento* no es lo suficientemente grande para contener el resultado especificado por *formato* y *argptr*, el valor devuelto de  **vsnprintf** es el número de caracteres que se escribiría, sin contar el carácter nulo, si *recuento* fuese lo suficientemente grande. Si el valor devuelto es mayor que *recuento* - 1, el resultado está truncado. Un valor devuelto de -1 indica que se produjo un error de codificación.

Ambos **_vsnprintf** y **_vsnwprintf** funciones devuelven el número de caracteres escritos si el número de caracteres que se va a escribir es menor o igual a *recuento*; si el número caracteres que se va a escribir es mayor que *recuento*, estas funciones devuelven -1 que indica que el resultado está truncado.

El valor devuelto por todas estas funciones no incluye el carácter nulo final, tanto si hay uno escrito como si no. Cuando *recuento* es cero, el valor devuelto es el número de caracteres que escribirían las funciones, no incluir ningún carácter nulo. Puede usar este resultado para asignar suficiente espacio de búfer para la cadena y su carácter nulo final y, luego, volver a llamar a la función para llenar el búfer.

Si *formato* es **NULL**, o si *búfer* es **NULL** y *recuento* no es igual a cero, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establezca **errno** a **EINVAL**.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones toma un puntero a una lista de argumentos, a continuación, da formato a los datos y escribe hasta *recuento* caracteres en la memoria que apunta *búfer*. El **vsnprintf** función siempre escribe un terminador nulo, aunque trunque el resultado. Cuando se usa **_vsnprintf** y **_vsnwprintf**, el búfer se termina en null solo si hay espacio al final (es decir, si el número de caracteres que se va a escribir es menor que *recuento*).

> [!IMPORTANT]
> Para evitar ciertos tipos de riesgos de seguridad, asegúrese de que *formato* no es una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

> [!NOTE]
> Para asegurarse de que hay espacio para el carácter nulo al llamar a **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** y **_vsnwprintf_l**, asegúrese de que *recuento* es estrictamente menor que la longitud del búfer e inicialice el búfer en null antes de llamar a la función.
>
> Dado que **vsnprintf** siempre escribe el terminador nulo, la *recuento* parámetro puede ser igual al tamaño del búfer.

A partir del UCRT en Visual Studio 2015 y Windows 10, **vsnprintf** ya no es idéntico al **_vsnprintf**. El **vsnprintf** función cumple con el estándar C99; **_vnsprintf** se conserva por compatibilidad con versiones anteriores con código antiguo de Visual Studio.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**, **_vsnprintf**, **_vsnprintf_l**|\<stdio.h>|\<stdio.h> o \<cstdio>|
|**_vsnwprintf**, **_vsnwprintf_l**|\<stdio.h> o \<wchar.h>|\<stdio.h>, \<wchar.h>, \<cstdio> o \<cwchar>|

El **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** y **_vsnwprintf_l** funciones son específicas de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

El comportamiento cambia si usa vsnprintf en su lugar, junto con los parámetros de cadena de caracteres estrechos. El *recuento* parámetro puede ser todo el tamaño del búfer y el valor devuelto es el número de caracteres que se hubieran escrito si *recuento* era lo suficientemente grande:

## <a name="example"></a>Ejemplo

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
[Sintaxis de especificación de formato: printf y wprintf (funciones)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
