---
title: _controlfp_s
ms.date: 04/05/2018
api_name:
- _controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 0d12c139f305a3c66419a4e27905ac9f73345f4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942878"
---
# <a name="_controlfp_s"></a>_controlfp_s

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

*mask*<br/>
Máscara de los bits de la nueva palabra de control que se va a definir.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto, o un código de error de valor **errno** .

## <a name="remarks"></a>Comentarios

La función **_controlfp_s** es una versión independiente de la plataforma y más segura de **_control87**, que obtiene la palabra de control de punto flotante en la dirección almacenada en *CurrentControl* y la establece mediante *newControl*. Los bits de los valores indican el estado de control de punto flotante. El estado de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante, en función de la plataforma. También puede usar **_controlfp_s** para enmascarar o desenmascarar las excepciones de punto flotante.

Si el valor de *Mask* es igual a 0, **_controlfp_s** obtiene la palabra de control de punto flotante y almacena el valor recuperado en *currentControl*.

Si *Mask* es distinto de cero, se establece un nuevo valor para la palabra de control: En el caso de cualquier bit que esté establecido (es decir, igual a 1) en *Mask*, el bit correspondiente en *New* se utiliza para actualizar la palabra de control. En otras palabras, *fpcntrl* = ((*fpcntrl* & ~*Mask*) &#124; (*máscara* *newControl* & )), donde *fpcntrl* es la palabra de control de punto flotante. En este escenario, *currentControl* se establece en el valor una vez completado el cambio; no es el antiguo valor de bit de palabra de control.

> [!NOTE]
> De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.

**_controlfp_s** es casi idéntico a la función **_Control87** en plataformas Intel (x86), x64 y ARM. Si tiene como destino plataformas x86, x64 o ARM, puede usar **_control87** o **_controlfp_s**.

La diferencia entre **_control87** y **_controlfp_s** es cómo tratan los valores desnormalizados. En el caso de las plataformas Intel (x86), x64 y ARM, **_control87** puede establecer y borrar la máscara de excepción de operando desnormalizado. **_controlfp_s** no modifica la máscara de excepción de operando desnormalizado. En este ejemplo se muestra la diferencia:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Los valores posibles de la constante de máscara (*máscara*) y los nuevos valores de control (*newControl*) se muestran en la siguiente tabla de valores hexadecimales. Use las constantes portables que se enumeran a continuación ( **_MCW_EM**, **_EM_INVALID**, etc.) como argumentos para estas funciones, en lugar de proporcionar los valores hexadecimales explícitamente.

Las plataformas derivadas de Intel (x86) admiten los valores de entrada y salida desnormalizados en el hardware. El comportamiento de x86 consiste en conservar los valores desnormalizados. La plataforma ARM y las plataformas x64 que tienen compatibilidad con SSE2 permiten que los operandos y resultados desnormalizados se vacíen o se fuercen a cero. Las funciones **_controlfp_s**, _ **controlfp**y **_control87** proporcionan una máscara para cambiar este comportamiento. En el siguiente ejemplo se muestra la forma de usar esta máscara:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

En las plataformas ARM, la función **_controlfp_s** se aplica al registro FPSCR. En las arquitecturas x64, solo se ve afectada la palabra de control SSE2 almacenada en el registro MXCSR. En las plataformas Intel (x86), **_controlfp_s** afecta a las palabras de control de X87 y SSE2, si existen. Es posible que las dos palabras de control sean incoherentes entre sí (debido a una llamada anterior a [__control87_2](control87-controlfp-control87-2.md), por ejemplo); Si hay una incoherencia entre las dos palabras de control, **_controlfp_s** establece la marca **EM_AMBIGUOUS** en *currentControl*. Se trata de una forma de advertir que la palabra de control devuelta podría no representar con precisión el estado de las dos palabras de control de punto flotante.

En las arquitecturas ARM y x64, no se admite el cambio del modo de infinito o la precisión de punto flotante. Si se usa la máscara de control de precisión en la plataforma x64, la función genera una aserción y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Si la máscara no se establece correctamente, esta función genera una excepción de parámetro no válido, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **EINVAL** y establece **errno** en **EINVAL**.

Esta función se omite cuando se usa [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) para compilar porque el Common Language Runtime (CLR) solo admite la precisión de punto flotante predeterminada.

### <a name="mask-constants-and-values"></a>Enmascarar valores y constantes

En el caso de la máscara **_MCW_EM** , si se desactiva, se establece la excepción, lo que permite la excepción de hardware. Si se establece, se oculta la excepción. Si se produce una **_EM_UNDERFLOW** o **_EM_OVERFLOW** , no se produce ninguna excepción de hardware hasta que se ejecute la siguiente instrucción de punto flotante. Para generar una excepción de hardware inmediatamente después de **_EM_UNDERFLOW** o **_EM_OVERFLOW**, llame a la instrucción de MASM FWAIT.

|Máscara|Valor hexadecimal|Constante|Valor hexadecimal|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Control desnormalizado)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Máscara de excepción de interrupción)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Control de infinito)<br /><br /> (No se admite en plataformas ARM o x64).|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Control de redondeo)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Control de precisión)<br /><br /> (No se admite en plataformas ARM o x64).|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

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
