---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348535"
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

*Máscara*<br/>
Máscara de los bits de la nueva palabra de control que se va a definir.

## <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente o un código de error de valor **errno.**

## <a name="remarks"></a>Observaciones

La función **_controlfp_s** es una versión más segura y independiente de la plataforma de **_control87**, que obtiene la palabra de control de punto flotante en la dirección que se almacena en *currentControl* y lo establece mediante *newControl*. Los bits de los valores indican el estado de control de punto flotante. El estado de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante, en función de la plataforma. También puede utilizar **_controlfp_s** para enmascarar o desenmascarar excepciones de punto flotante.

Si el valor de *mask* es igual a 0, **_controlfp_s** obtiene la palabra de control de punto flotante y almacena el valor recuperado en *currentControl*.

Si *mask* es distinto de cero, se establece un nuevo valor para la palabra de control: para cualquier bit que se establece (es decir, igual a 1) en *máscara,* se utiliza el bit correspondiente en *new* para actualizar la palabra de control. En otras palabras, *fpcntrl* ((*fpcntrl* & -*mask*) &#124;*(newControl* & *mask*)) donde *fpcntrl* es la palabra de control de punto flotante. En este escenario, *currentControl* se establece en el valor una vez completado el cambio; no es el antiguo valor de bit de palabra de control.

> [!NOTE]
> De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.

**_controlfp_s** es casi idéntica a la función **_control87** en las plataformas Intel (x86), x64 y ARM. Si tiene como destino plataformas x86, x64 o ARM, puede utilizar **_control87** o **_controlfp_s.**

La diferencia entre **_control87** y **_controlfp_s** está en cómo tratan los valores desnormales. Para las plataformas Intel (x86), x64 y ARM, **_control87** puede establecer y borrar la máscara de excepción DENORMAL OPERAND. **_controlfp_s** no modifica la máscara de excepción DENORMAL OPERAND. En este ejemplo se muestra la diferencia:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Los valores posibles para la constante de máscara (*máscara*) y los nuevos valores de control (*newControl*) se muestran en la siguiente tabla Valores hexadecimales. Utilice las constantes portátiles enumeradas a continuación **(_MCW_EM**, **_EM_INVALID**, etc.) como argumentos para estas funciones, en lugar de proporcionar los valores hexadecimales explícitamente.

Las plataformas derivadas de Intel (x86) admiten los valores de entrada y salida desnormalizados en el hardware. El comportamiento de x86 consiste en conservar los valores desnormalizados. La plataforma ARM y las plataformas x64 que tienen compatibilidad con SSE2 permiten vaciar los operandos Y resultados DENORMALes o forzarlos a cero. Las funciones **_controlfp_s**, **_controlfp**y **_control87** proporcionan una máscara para cambiar este comportamiento. En el siguiente ejemplo se muestra la forma de usar esta máscara:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

En las plataformas ARM, la función **_controlfp_s** se aplica al registro FPSCR. En las arquitecturas x64, solo se ve afectada la palabra de control SSE2 que se almacena en el registro MXCSR. En las plataformas Intel (x86), **_controlfp_s** afecta a las palabras de control para el x87 y el SSE2, si está presente. Es posible que las dos palabras de control sean incompatibles entre sí (debido a una llamada anterior a [__control87_2,](control87-controlfp-control87-2.md)por ejemplo); si hay una incoherencia entre las dos palabras de control, **_controlfp_s** establece el **EM_AMBIGUOUS** marca en *currentControl*. Se trata de una forma de advertir que la palabra de control devuelta podría no representar con precisión el estado de las dos palabras de control de punto flotante.

En las arquitecturas ARM y x64, no se admite el cambio del modo infinito o la precisión de punto flotante. Si se utiliza la máscara de control de precisión en la plataforma x64, la función genera una aserción y se invoca el controlador de parámetros no válidos, como se describe en Validación de [parámetros](../../c-runtime-library/parameter-validation.md).

Si la máscara no se establece correctamente, esta función genera una excepción de parámetro no válido, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **EINVAL** y establece **errno** en **EINVAL**.

Esta función se omite cuando se usa [/clr (Compilación](../../build/reference/clr-common-language-runtime-compilation.md) de Common Language Runtime) para compilar porque Common Language Runtime (CLR) solo admite la precisión de punto flotante predeterminada.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Constantes y valores de máscara

Para la **máscara de _MCW_EM,** borrarla establece la excepción, lo que permite la excepción de hardware; establecerlo oculta la excepción. Si se produce un **_EM_UNDERFLOW** o **_EM_OVERFLOW,** no se produce ninguna excepción de hardware hasta que se ejecuta la siguiente instrucción de punto flotante. Para generar una excepción de hardware inmediatamente después de **_EM_UNDERFLOW** o **_EM_OVERFLOW**, llame a la instrucción FWAIT MASM.

|Máscara|Valor hexadecimal|Constante|Valor hexadecimal|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (control desnormal)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (interrumpir máscara de excepción)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (control infinito)<br /><br /> (No compatible con plataformas ARM o x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (control de redondeo)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (control de precisión)<br /><br /> (No compatible con plataformas ARM o x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
