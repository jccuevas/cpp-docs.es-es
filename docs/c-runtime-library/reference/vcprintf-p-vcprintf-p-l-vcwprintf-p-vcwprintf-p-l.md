---
title: _vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _vcprintf_p
- _vcwprintf_p_l
- _vcprintf_p_l
- _vcwprintf_p
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
apitype: DLLExport
f1_keywords:
- vcwprintf_p
- vcprintf_p_l
- _vcprintf_p
- _vcprintf_p_l
- vcwprintf_p_l
- vcprintf_p
- _vcwprintf_p
- _vcwprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- _vtcprintf_p_l function
- vcprintf_p_l function
- _vcprintf_p_l function
- vtcprintf_p_l function
- vcprintf_p function
- _vcwprintf_p function
- _vcprintf_p function
- vcwprintf_p function
- vcwprintf_p_l function
- vtcprintf_p function
- _vcwprintf_p_l function
- _vtcprintf_p function
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6de7e419ba0c347092ac4f64296d81fef08745dc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="vcprintfp-vcprintfpl-vcwprintfp-vcwprintfpl"></a>_vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l

Escribe la salida con formato en la consola mediante un puntero a una lista de argumentos y admite parámetros posicionales en la cadena de formato.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _vcprintf_p(
   const char* format,
   va_list argptr
);
int _vcprintf_p_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf_p(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_p_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Especificación de formato.

*argptr*<br/>
Puntero a una lista de argumentos.

*locale*<br/>
Configuración regional que se va a usar.

Para obtener más información, vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

Número de caracteres escritos o un valor negativo si se produce un error en la salida. Si *formato* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y se devuelve -1.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, utiliza el **_putch** función para dar formato y escribir los datos especificados en la consola. (**_vcwprintf_p** utiliza **_putwch** en lugar de **_putch**. **_vcwprintf_p** es la versión con caracteres anchos de **_vcprintf_p**. Toma una cadena de caracteres anchos como argumento).

Las versiones de estas funciones que tienen la **_l** sufijo son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual.

Cada *argumento* (si existe) se convierte y se muestra según la especificación de formato correspondiente de *formato*. La especificación de formato admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato. Para obtener más información, consulte [printf_p (Parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md).

Estas funciones no convierten los caracteres de avance de línea en combinaciones retorno de carro-avance de línea (CR-LF) cuando producen valores de salida.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

Estas funciones validan el puntero de entrada y la cadena de formato. Si *formato* o *argumento* es **NULL**, o si la cadena de formato contiene caracteres de formato no válidos, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_vtcprintf_p**|**_vcprintf_p**|**_vcprintf_p**|**_vcwprintf_p**|
|**_vtcprintf_p_l**|**_vcprintf_p_l**|**_vcprintf_p_l**|**_vcwprintf_p_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_vcprintf_p**, **_vcprintf_p_l**|\<conio.h> y \<stdarg.h>|
|**_vcwprintf_p**, **_vcwprintf_p_l**|\<conio.h> y \<stdarg.h>|

Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_vcprintf_p.c
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function that's used to print to the console.
int eprintf(const char* format, ...)
{
   va_list args;
   va_start(args, format);
   int result = _vcprintf_p(format, args);
   va_end(args);
   return result;
}

int main()
{
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",
      "one", 222);
   _cprintf_s("%d characters printed\r\n");
}
```

```Output
parameter 2 = 222; parameter 1 = one
38 characters printed
```

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p (parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
