---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 255c3b760dec1495a4f9a82915878a5504844f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188731"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Escribe un resultado con formato mediante un puntero a una lista de argumentos. Estas son versiones de [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento del resultado.

*sizeOfBuffer*<br/>
El tamaño de la *búfer* para la salida, como el recuento de caracteres.

*count*<br/>
Número máximo de caracteres que se van a escribir (sin incluir el valor final nulo), o [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Especificación de formato.

*argptr*<br/>
Puntero a la lista de argumentos.

*locale*<br/>
Configuración regional que se va a usar.

Para más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

**vsnprintf_s**, **_vsnprintf_s** y **_vsnwprintf_s** devuelve el número de caracteres escritos, sin incluir el carácter nulo final o un valor negativo si se produce un error de salida. **vsnprintf_s** es idéntico al **_vsnprintf_s**. **vsnprintf_s** se incluye para garantizar el cumplimiento del estándar ANSI. **_vnsprintf** se conserva por compatibilidad con versiones anteriores.

Si supera el almacenamiento necesario para almacenar los datos y un carácter nulo final *sizeOfBuffer*, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md), a menos que *recuento*  es [_TRUNCATE](../../c-runtime-library/truncate.md), en cuyo caso gran parte de la cadena que quepa *búfer* se escribe y devuelve -1. Si la ejecución continúa después del controlador de parámetros no válidos, estas funciones establecen *búfer* en una cadena vacía, establece **errno** a **ERANGE**y devuelven -1.

Si *búfer* o *formato* es un **NULL** puntero, o si *recuento* es menor o igual a cero, se invoca el controlador de parámetros no válidos. Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

### <a name="error-conditions"></a>Condiciones de error

|**condición**|Volver|**errno**|
|-----------------|------------|-------------|
|*búfer* es **NULL**|-1|**EINVAL**|
|*formato* es **NULL**|-1|**EINVAL**|
|*count* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* demasiado pequeño (y *recuento* ! = **_TRUNCATE**)|-1 (y *búfer* establecido en una cadena vacía)|**ERANGE**|

## <a name="remarks"></a>Comentarios

Cada una de estas funciones toma un puntero a una lista de argumentos, a continuación, da formato y escribe hasta *recuento* caracteres de los datos especificados en la memoria que apunta *búfer* y anexa un carácter nulo final.

Si *recuento* es [_TRUNCATE](../../c-runtime-library/truncate.md), estas funciones escriben la parte de la cadena que quepa en *búfer* , dejando espacio para un carácter nulo. Si toda la cadena (con valor nulo final) cabe *búfer*, a continuación, estas funciones devuelven el número de caracteres escritos (sin incluir el carácter nulo final); en caso contrario, estas funciones devuelven -1 para indicar que el truncamiento se ha producido.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

> [!NOTE]
> Para asegurarse de que hay espacio para el carácter nulo final, asegúrese de que *recuento* es estrictamente menor que la longitud del búfer, o use **_TRUNCATE**.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> y \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> y \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> o \<wchar.h> y \<stdarg.h>|\<varargs.h>*|

\* Necesario para la compatibilidad con UNIX V.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
