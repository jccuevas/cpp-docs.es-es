---
title: _controlfp_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- controlfp_s
- _controlfp_s
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 443b9ee53606bc3075e62e98012edfca79747cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405096"
---
# <a name="controlfps"></a>_controlfp_s

Obtiene y establece la palabra de control de punto flotante. Estas versiones de [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parámetros

*currentControl*<br/>
Valor actual del bit de palabra de control.

*newControl*<br/>
Valores de bit de la nueva palabra de control.

*máscara*<br/>
Máscara de los bits de la nueva palabra de control que se va a definir.

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente, o un **errno** valor de código de error.

## <a name="remarks"></a>Comentarios

El **_controlfp_s** función es una versión independiente de la plataforma y más segura de **_control87**, que inserta la palabra de control de punto flotante en la dirección que se almacena en  *currentControl* y se establece mediante el uso de *newControl*. Los bits de los valores indican el estado de control de punto flotante. El estado de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante, en función de la plataforma. También puede usar **_controlfp_s** a o quitar una máscara excepciones de punto flotante.

Si el valor de *máscara* es igual a 0, **_controlfp_s** Obtiene la palabra de control de punto flotante y almacena el valor recuperado en *currentControl*.

Si *máscara* es distinto de cero, se establece un nuevo valor para la palabra de control: para cualquier bit que se establece (es decir, igual a 1) en *máscara*, el bit correspondiente en *nueva* se utiliza para actualizar el control Word. En otras palabras, *fpcntrl* = ((*fpcntrl* & ~*máscara*) &#124; (*newControl* & *máscara* )) donde *fpcntrl* es la palabra de control de punto flotante. En este escenario, *currentControl* se establece en el valor una vez finaliza el cambio; no es el valor de bit de palabra de control anterior.

> [!NOTE]
> De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.

**_controlfp_s** es casi idéntica a la **_control87** función Intel (x86), x64 y las plataformas ARM. Si se dirige a x86, x64 o plataformas ARM, puede usar **_control87** o **_controlfp_s**.

La diferencia entre **_control87** y **_controlfp_s** es cómo tratan los valores desnormalizados. Intel (x86), x 64 y las plataformas ARM, **_control87** puede establecer y borrar la máscara de excepción de OPERANDO DESNORMALIZADO. **_controlfp_s** no modifica la máscara de excepción de OPERANDO DESNORMALIZADO. En este ejemplo se muestra la diferencia:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Los valores posibles para la constante de máscara (*máscara*) y nuevos valores de control (*newControl*) se muestran en la siguiente tabla de valores hexadecimales. Use las constantes portables que se enumeran a continuación (**_MCW_EM**, **_EM_INVALID**, etc.) como argumentos para estas funciones, en lugar de proporcionar el valor hexadecimal valores explícitamente.

Las plataformas derivadas de Intel (x86) admiten los valores de entrada y salida desnormalizados en el hardware. El comportamiento de x86 consiste en conservar los valores desnormalizados. La plataforma ARM y la x64 admiten plataformas con SSE2 permiten DESNORMALIZADOS operandos y resultados se vacían, o obligado a cero. El **_controlfp_s**, **_controlfp**, y **_control87** funciones proporcionan una máscara para cambiar este comportamiento. En el siguiente ejemplo se muestra la forma de usar esta máscara:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

En plataformas ARM, el **_controlfp_s** función se aplica en el registro fpscr. En x64 arquitecturas, solo la palabra de control de SSE2 se almacena en el MXCSR se ve afectado el registro. En plataformas Intel (x86), **_controlfp_s** afecta a las palabras de control de x87 y SSE2, si está presente. Es posible que las dos palabras de control no sean iguales entre sí (debido a una llamada anterior a [__control87_2](control87-controlfp-control87-2.md), por ejemplo); si hay una incoherencia entre las dos palabras de control, **_controlfp_s** establece la **EM_AMBIGUOUS** se marcan en *currentControl*. Se trata de una forma de advertir que la palabra de control devuelta podría no representar con precisión el estado de las dos palabras de control de punto flotante.

En el BRAZO y x64 arquitecturas, cambiar el modo de infinito o la precisión de punto flotante no es compatible. Si se usa la máscara de control de precisión en la x64 plataforma, la función genera una aserción y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Si la máscara no se establece correctamente, esta función genera una excepción de parámetro no válido, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **EINVAL** y establece **errno** a **EINVAL**.

Esta función se omite cuando usa [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) al compilarse porque common language runtime (CLR) solo es compatible con la precisión de punto flotante predeterminada.

### <a name="mask-constants-and-values"></a>Constantes de máscara y valores

Para el **_MCW_EM** máscara, al desactivarla, Establece la excepción, lo que permite la excepción de hardware, se oculta la excepción. Si un **_EM_UNDERFLOW** o **_EM_OVERFLOW** se produce, se inicia ninguna excepción de hardware hasta que se ejecute la siguiente instrucción de punto flotante. Para generar una excepción de hardware inmediatamente después de **_EM_UNDERFLOW** o **_EM_OVERFLOW**, llame a la instrucción FWAIT MASM.

|Máscara|Valor hexadecimal|Constante|Valor hexadecimal|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (control desnormalizado)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (máscara de la excepción de interrupción)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (control de infinito)<br /><br /> (No en ARM o x64 las plataformas admitidas.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (control de redondeo)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (control de precisión)<br /><br /> (No en ARM o x64 las plataformas admitidas.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
