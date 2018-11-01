---
title: _cputs, _cputws
ms.date: 11/04/2016
apiname:
- _cputws
- _cputs
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cputws
- _cputs
- _cputws
helpviewer_keywords:
- strings [C++], writing
- _cputs function
- _cputws function
- putting strings to the console
- cputs function
- console, sending strings to
- cputws function
ms.assetid: ec418484-0f8d-43ec-8d8b-198a556c659e
ms.openlocfilehash: 81d2364cd1fc409ca3267bc416bd3cbd16c62a15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601180"
---
# <a name="cputs-cputws"></a>_cputs, _cputws

Coloca una cadena en la consola.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _cputs(
   const char *str
);
int _cputws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena de salida

## <a name="return-value"></a>Valor devuelto

Si es correcto, **_cputs** devuelve 0. Si se produce un error en la función, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

El **_cputs** función escribe la cadena terminada en null que apunta *str* directamente en la consola. No se anexa ninguna combinación de retorno de carro y salto de línea (CR-LF) automáticamente a la cadena.

Esta función valida su parámetro. Si *str* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y se devuelve -1.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cputts**|**_cputs**|**_cputs**|**_cputws**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_cputs**|\<conio.h>|\<errno.h>|
|**_cputws**|\<conio.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_cputs.c
// compile with: /c
// This program first displays a string to the console.

#include <conio.h>
#include <errno.h>

void print_to_console(char* buffer)
{
   int retval;
   retval = _cputs( buffer );
   if (retval)
   {
       if (errno == EINVAL)
       {
         _cputs( "Invalid buffer in print_to_console.\r\n");
       }
       else
         _cputs( "Unexpected error in print_to_console.\r\n");
   }
}

void wprint_to_console(wchar_t* wbuffer)
{
   int retval;
   retval = _cputws( wbuffer );
   if (retval)
   {
       if (errno == EINVAL)
       {
         _cputws( L"Invalid buffer in wprint_to_console.\r\n");
       }
       else
         _cputws( L"Unexpected error in wprint_to_console.\r\n");
   }
}

int main()
{

   // String to print at console.
   // Notice the \r (return) character.
   char* buffer = "Hello world (courtesy of _cputs)!\r\n";
   wchar_t *wbuffer = L"Hello world (courtesy of _cputws)!\r\n";
   print_to_console(buffer);
   wprint_to_console( wbuffer );
}
```

```Output
Hello world (courtesy of _cputs)!
Hello world (courtesy of _cputws)!
```

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_putch, _putwch](putch-putwch.md)<br/>
