---
title: _control87, _controlfp, __control87_2
ms.date: 08/29/2019
api_name:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: 15700a5dabfbc3f8915e251bd8b9270f8f9c1a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942901"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87, _controlfp, __control87_2

Obtiene y establece la palabra de control de punto flotante. Hay disponible una versión más segura de _ **controlfp** ; vea [_controlfp_s](controlfp-s.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>Parámetros

*new*\
Valores de bit de la nueva palabra de control.

*máscara*\
Máscara de los bits de la nueva palabra de control que se va a definir.

*x86_cw*\
Se llena con la palabra de control de la unidad de punto flotante x87. Pase 0 (**null**) para establecer solo la palabra de control SSE2.

*sse2_cw*\
Palabra de control de la unidad de punto flotante de SSE. Pase 0 (**null**) para establecer solo la palabra de control x87.

## <a name="return-value"></a>Valor devuelto

En el caso de **_control87** y _ **controlfp**, los bits del valor devuelto indican el estado de control de punto flotante. Para obtener una definición completa de los bits devueltos por **_control87**, consulte float. C.

En el caso de **__control87_2**, el valor devuelto es 1, que indica que la operación se ha realizado correctamente.

## <a name="remarks"></a>Comentarios

La función **_control87** obtiene y establece la palabra de control de punto flotante. La palabra de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito, en función de la plataforma. También puede usar **_control87** para enmascarar o desenmascarar las excepciones de punto flotante. Si el valor de *Mask* es igual a 0, **_control87** obtiene la palabra de control de punto flotante. Si *Mask* es distinto de cero, se establece un nuevo valor para la palabra de control: En el caso de cualquier bit que esté activado (es decir, igual a 1) en *Mask*, el bit correspondiente en *New* se utiliza para actualizar la palabra de control. En otras palabras, **fpcntrl** = ((**fpcntrl** & ~*Mask*) &#124; (*nueva* & *máscara*)), donde **fpcntrl** es la palabra de control de punto flotante.

> [!NOTE]
> De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.

_ **controlfp** es una versión portátil e independiente de la plataforma de **_control87** que es prácticamente idéntica a la función **_control87** . Si el código tiene como destino más de una plataforma, use _ **controlfp** o **_controlfp_s**. La diferencia entre **_control87** y _ **controlfp** es cómo tratan los valores desnormalizados. En las plataformas x86, x64, ARM y ARM64, **_control87** puede establecer y borrar la máscara de excepción de operando desnormalizado. _ **controlfp** no modifica la máscara de excepción de operando desnormalizado. En este ejemplo se muestra la diferencia:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Los valores posibles de la constante de máscara (*máscara*) y los nuevos valores de control (*nuevo*) se muestran en la tabla control de valores y valores de palabra. Use las constantes portables que se enumeran a continuación ( **_MCW_EM**, **_EM_INVALID**, etc.) como argumentos para estas funciones, en lugar de proporcionar los valores hexadecimales explícitamente.

Las plataformas derivadas de Intel x86 admiten los valores de entrada y salida desnormalizados en el hardware. El comportamiento de x86 consiste en conservar los valores desnormalizados. Las plataformas ARM y ARM64 y las plataformas x64 que tienen compatibilidad con SSE2 permiten que los operandos y resultados desnormalizados se vacíen o se fuercen a cero. Las funciones _ **controlfp** y **_control87** proporcionan una máscara para cambiar este comportamiento. En el siguiente ejemplo se muestra la forma de usar esta máscara.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

En las plataformas ARM y ARM64, las funciones **_control87** e _ **controlfp** se aplican al registro FPSCR. Solo la palabra de control SSE2 almacenada en el registro MXCSR se ve afectada en plataformas x64. En las plataformas x86, **_control87** y _ **controlfp** afectan a las palabras de control de x87 y SSE2, si existen.

La función **__control87_2** permite controlar las unidades de punto flotante de X87 y SSE2 juntas o por separado. Para afectar ambas unidades, pase las direcciones de dos enteros a **x86_cw** y **sse2_cw**. Si solo quiere afectar a una unidad, pase una dirección para ese parámetro, pero pase 0 (**null**) para el otro. Si se pasa 0 para uno de estos parámetros, la función no tiene ningún efecto en esa unidad de punto flotante. Resulta útil cuando parte del código usa la unidad de punto flotante x87 y otra parte usa la unidad de punto flotante SSE2.

Si usa **__control87_2** para establecer valores diferentes para las palabras de control de punto flotante, es posible que **_control87** o _ **controlfp** no puedan devolver una sola palabra de control para representar el estado de las dos unidades de punto flotante. En tal caso, estas funciones establecen la marca **EM_AMBIGUOUS** en el valor entero devuelto para indicar una incoherencia entre las dos palabras de control. La marca **EM_AMBIGUOUS** es una advertencia de que la palabra de control devuelta podría no representar con precisión el estado de ambas palabras de control de punto flotante.

En las plataformas ARM, ARM64 y x64, no se admite el cambio del modo de infinito o la precisión de punto flotante. Si se usa la máscara de control de precisión en la plataforma x64, la función genera una aserción y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** no se admite en las plataformas ARM, ARM64 o x64. Si usa **__control87_2** y compila el programa para las plataformas ARM, ARM64 o x64, el compilador genera un error.

Estas funciones se omiten cuando se usa [/CLR (Common Language Runtime](../../build/reference/clr-common-language-runtime-compilation.md) Compilation) para compilar. El Common Language Runtime (CLR) solo admite la precisión de punto flotante predeterminada.

### <a name="control-word-masks-and-values"></a>Controlar los valores y las máscaras de palabras

En el caso de la máscara **_MCW_EM** , al borrar la máscara se establece la excepción, lo que permite la excepción de hardware. Si se establece la máscara, se oculta la excepción. Si se produce una **_EM_UNDERFLOW** o **_EM_OVERFLOW** , no se produce ninguna excepción de hardware hasta que se ejecute la siguiente instrucción de punto flotante. Para generar una excepción de hardware inmediatamente después de **_EM_UNDERFLOW** o **_EM_OVERFLOW**, llame a la instrucción de MASM **FWAIT** .

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
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)\
[_clear87, _clearfp](clear87-clearfp.md)\
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
