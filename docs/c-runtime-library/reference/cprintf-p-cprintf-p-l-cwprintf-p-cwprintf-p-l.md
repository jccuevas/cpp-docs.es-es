---
title: _cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l
ms.date: 11/04/2016
apiname:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
ms.openlocfilehash: ef4ac6a89749c2784e4935fcf83810e81b61ae11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658463"
---
# <a name="cprintfp-cprintfpl-cwprintfp-cwprintfpl"></a>_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l

Da formato e imprime en la consola, y admite parámetros posicionales en la cadena de formato.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _cprintf_p(
   const char * format [,
   argument] ...
);
int _cprintf_p_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_p(
   const wchar * format [,
   argument] ...
);
int _cwprintf_p_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Cadena de control de formato.

*argumento*<br/>
Parámetros opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Número de caracteres impreso o un valor negativo si se produce un error.

## <a name="remarks"></a>Comentarios

Estas funciones de formato e imprimir una serie de caracteres y valores directamente en la consola, utilizando el **_putch** y **_putwch** funciones para generar caracteres. Cada *argumento* (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. El formato tiene las mismas forma y función que el *formato* parámetro para el [printf_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) función. La diferencia entre **_cprintf_p** y **cprintf_s** es que **_cprintf_p** admite parámetros posicionales, lo que permite especificar el orden en que los argumentos son se utiliza en la cadena de formato. Para obtener más información, consulte [printf_p (Parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md).

A diferencia de la **fprintf_p**, **printf_p**, y **sprintf_p** funciones, ni **_cprintf_p** ni **_cwprintf_p** traduce los caracteres de avance de línea al carro combinaciones de retorno y salto de línea (CR-LF) cuando la salida. Una diferencia importante es que **_cwprintf_p** muestra caracteres Unicode cuando se usa en Windows NT. A diferencia de **_cprintf_p**, **_cwprintf_p** usa la configuración regional actual de consola.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

Además, al igual que **_cprintf_s** y **_cwprintf_s**, validan el puntero de entrada y la cadena de formato. Si *formato* o *argumento* son **NULL**, o del formato de cadena contiene caracteres de formato no válidos, estas funciones invocan el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establezca **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_p**|**_cprintf_p**|**_cprintf_p**|**_cwprintf_p**|
|**_tcprintf_p_l**|**_cprintf_p_l**|**_cprintf_p_l**|**_cwprintf_p_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cprintf_p**, **_cprintf_p_l**|\<conio.h>|
|**_cwprintf_p**, **_cwprintf_p_l**|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cprintf_p.c
// This program displays some variables to the console
// using the _cprintf_p function.

#include <conio.h>

int main( void )
{
    int         i = -16,
                h = 29;
    unsigned    u = 62511;
    char        c = 'A';
    char        s[] = "Test";

    // Note that console output does not translate
    // \n as standard output does. Use \r\n instead.
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",
                h, i, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)<br/>
[_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p (parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[Sintaxis de especificación de formato: printf y wprintf (funciones)](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
