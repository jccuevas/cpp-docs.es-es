---
title: _control87, _controlfp, __control87_2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48d0c3107bf2edc09017ea138e4c8024ce328dd8
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2

Obtiene y establece la palabra de control de punto flotante. Una versión más segura de **_controlfp** está disponible; vea [_controlfp_s](controlfp-s.md).

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

*new*<br/>
Valores de bit de la nueva palabra de control.

*máscara*<br/>
Máscara de los bits de la nueva palabra de control que se va a definir.

*x86_cw*<br/>
Se llena con la palabra de control de la unidad de punto flotante x87. Pase 0 (**NULL**) para establecer solo la palabra de control de SSE2.

*sse2_cw*<br/>
Palabra de control de la unidad de punto flotante de SSE. Pase 0 (**NULL**) para establecer solo x87 palabra de control.

## <a name="return-value"></a>Valor devuelto

Para **_control87** y **_controlfp**, los bits en el valor devuelven indican el estado de control de punto flotante. Para ver una definición completa de los bits devueltos por **_control87**, vea FLOAT. H.

Para **__control87_2**, el valor devuelto es 1, que indica una ejecución correcta.

## <a name="remarks"></a>Comentarios

El **_control87** función obtiene y establece la palabra de control de punto flotante. La palabra de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante, en función de la plataforma. También puede usar **_control87** a o quitar una máscara excepciones de punto flotante. Si el valor de *máscara* es igual a 0, **_control87** Obtiene la palabra de control de punto flotante. Si *máscara* es distinto de cero, se establece un nuevo valor para la palabra de control: para cualquier bit que se encuentra en (es decir, igual a 1) en *máscara*, el bit correspondiente en *nueva* se utiliza para actualizar el control Word. En otras palabras, **fpcntrl** = ((**fpcntrl** & ~*máscara*) &#124; (*nueva* & *máscara*)) donde **fpcntrl** es la palabra de control de punto flotante.

> [!NOTE]
> De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.

**_controlfp** es una versión independiente de la plataforma y portable de **_control87**. Es casi idéntica a la **_control87** función en plataformas ARM, x64 y x86. Si se dirige a x86, x64 o plataformas ARM, utilice **_control87** o **_controlfp**.

La diferencia entre **_control87** y **_controlfp** es cómo tratan los valores DESNORMALIZADOS. Para x86, x64 y las plataformas ARM, **_control87** puede establecer y borrar la máscara de excepción de OPERANDO DESNORMALIZADO. **_controlfp** no modifica la máscara de excepción de OPERANDO DESNORMALIZADO. En este ejemplo se muestra la diferencia:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Los valores posibles para la constante de máscara (*máscara*) y nuevos valores de control (*nueva*) se muestran en la siguiente tabla de valores hexadecimales. Use las constantes portables que se enumeran a continuación (**_MCW_EM**, **_EM_INVALID**, etc.) como argumentos para estas funciones, en lugar de proporcionar el valor hexadecimal valores explícitamente.

Plataformas x86 derivadas de Intel admiten la DESNORMALIZADOS entrada y salida en el hardware. El comportamiento de x86 consiste en conservar los valores desnormalizados. La plataforma ARM y la x64 admiten plataformas con SSE2 permiten DESNORMALIZADOS operandos y resultados se vacían, o obligado a cero. El **_controlfp** y **_control87** funciones proporcionan una máscara para cambiar este comportamiento. En el siguiente ejemplo se muestra la forma de usar esta máscara.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

En plataformas ARM, el **_control87** y **_controlfp** aplican las funciones para el registro fpscr. En x64 arquitecturas, solo la palabra de control de SSE2 se almacena en el MXCSR se ve afectado el registro. En x86 plataformas, **_control87** y **_controlfp** afectan a las palabras de control de x87 y SSE2, si está presente. La función **__control87_2** permite x87 y unidades de punto flotante SSE2 controlar conjuntamente o por separado. Si desea que afecte a las unidades, pase las direcciones de dos enteros a **x86_cw** y **sse2_cw**. Si solo desea afectar a una unidad, pase una dirección para ese parámetro y pase 0 (**NULL**) para los demás. Si se pasa 0 para uno de estos parámetros, la función no tiene ningún efecto en esa unidad de punto flotante. Esta funcionalidad podría ser útil en situaciones en la que parte del código usa la unidad de punto flotante x87 y otra parte usa la unidad de punto flotante SSE2. Si usa **__control87_2** en una parte de un programa y establecer valores diferentes para las palabras de control de punto flotante y, a continuación, utilizar **_control87** o **_controlfp** para seguir manipular la palabra de control, a continuación, **_control87** y **_controlfp** es posible que pueda devolver una sola palabra de control para representar el estado de las unidades de punto flotante. En tal caso, estas funciones establecen los **EM_AMBIGUOUS** marca en el valor entero devuelto para indicar que hay una incoherencia entre las dos palabras de control. Se trata de una forma de advertir que la palabra de control devuelta podría no representar con precisión el estado de las dos palabras de control de punto flotante.

En el BRAZO y x64 arquitecturas, cambiar el modo de infinito o la precisión de punto flotante no es compatible. Si se usa la máscara de control de precisión en la x64 plataforma, la función genera una aserción y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** no se admite en el BRAZO o x64 arquitecturas. Si usa **__control87_2** y compilar el programa para la ARM o x64 arquitecturas, el compilador genera un error.

Estas funciones se omiten cuando usa [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) al compilarse porque common language runtime (CLR) solo es compatible con la precisión de punto flotante predeterminada.

**Valores hexadecimales**

Para el **_MCW_EM** máscara, borrar la máscara establece la excepción, lo que permite la excepción de hardware; establezca la máscara oculta la excepción. Si un **_EM_UNDERFLOW** o **_EM_OVERFLOW** se produce, se inicia ninguna excepción de hardware hasta que se ejecute la siguiente instrucción de punto flotante. Para generar una excepción de hardware inmediatamente después de **_EM_UNDERFLOW** o **_EM_OVERFLOW**, llame a la **FWAIT** instrucción de MASM.

|Máscara|Valor hexadecimal|Constante|Valor hexadecimal|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (control desnormalizado)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (máscara de la excepción de interrupción)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (control de infinito)<br /><br /> (No se admite en ARM o x64] plataformas.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (control de redondeo)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (control de precisión)<br /><br /> (No en ARM o x64 las plataformas admitidas.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cntrl87.c
// processor: x86
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87;

    // Show original x87 control word and do calculation.
    control_word_x87 = __control87_2(0, 0,
                                     &control_word_x87, 0);
    printf( "Original: 0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    control_word_x87 = __control87_2(_PC_24, MCW_PC,
                                     &control_word_x87, 0);
    printf( "24-bit:   0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,
                                     &control_word_x87, 0 );
    printf( "Default:  0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0001
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0x0001
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x0001
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
