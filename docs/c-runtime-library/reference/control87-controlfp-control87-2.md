---
title: "_control87, _controlfp, __control87_2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_control87"
  - "_controlfp"
  - "__control87_2"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_control87"
  - "__control87_2"
  - "control87"
  - "_controlfp"
  - "controlfp"
  - "control87_2"
  - "_control87_2"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__control87_2 (función)"
  - "_control87 (función)"
  - "_controlfp (función)"
  - "control87 (función)"
  - "control87_2 (función)"
  - "controlfp (función)"
  - "EM_AMBIGUOUS"
  - "funciones de punto flotante"
  - "funciones de punto flotante, establecer palabra de control"
  - "números de punto flotante, palabra de control"
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: 34
caps.handback.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _control87, _controlfp, __control87_2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene y establece la palabra de control de punto flotante.  Hay disponible una versión más segura de `_controlfp`; vea [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md).  
  
## Sintaxis  
  
```  
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
  
#### Parámetros  
 `new`  
 Valores de bit de la nueva palabra de control.  
  
 `mask`  
 Máscara de los bits de la nueva palabra de control que se va a definir.  
  
 `x86_cw`  
 Se llena con la palabra de control de la unidad de punto flotante x87.  Pase 0 \(`NULL`\) para establecer solo la palabra de control de SSE2.  
  
 `sse2_cw`  
 Palabra de control de la unidad de punto flotante de SSE.  Pase 0 \(`NULL`\) para establecer solo la palabra de control de x87.  
  
## Valor devuelto  
 En el caso de `_control87` y `_controlfp`, los bits del valor devuelto indican el estado de control del punto flotante.  Para ver una definición completa de los bits que devuelve `_control87`, vea FLOAT.H.  
  
 En el caso de `__control87_2`, el valor devuelto es 1, que indica que la operación ha sido correcta.  
  
## Comentarios  
 La función `_control87` obtiene y establece la palabra de control de punto flotante.  La palabra de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante, en función de la plataforma.  También puede utilizar `_control87` para aplicar o quitar una máscara a excepciones de punto flotante.  Si el valor de `mask` es igual a 0, `_control87` obtiene la palabra de control de punto flotante.  Si `mask` es distinto de cero, se establece un nuevo valor para la palabra de control: en el caso de cualquier bit que esté activado \(es decir, que sea igual a 1\) en `mask`, se usa el bit correspondiente de `new` para actualizar la palabra de control.  Dicho de otro modo, `fpcntrl` `=` \(\(`fpcntrl` `& ~mask`\) &#124; \(`new & mask`\)\), donde `fpcntrl` es la palabra de control de punto flotante.  
  
> [!NOTE]
>  De forma predeterminada, las bibliotecas en tiempo de ejecución aplican máscaras a todas las excepciones de punto flotante.  
  
 `_controlfp` es una versión independiente de la plataforma y portable de `_control87`.  Es casi idéntica a la función `_control87` de las plataformas Intel \(x86\), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] y ARM.  Si tiene como destino las plataformas x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] o ARM, use `_control87` o `_controlfp`.  
  
 La diferencia entre `_control87` y `_controlfp` es cómo tratan los valores desnormalizados.  En el caso de las plataformas Intel \(x86\), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] y ARM, `_control87` puede establecer y borrar la máscara de la excepción de operando desnormalizado.  `_controlfp` no modifica la máscara de la excepción de operando desnormalizado.  En este ejemplo se muestra la diferencia:  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 Los valores posibles de la constante de máscara \(`mask`\) y los nuevos valores de control \(`new`\) se muestran en la siguiente tabla de valores hexadecimales.  Use las constantes portables que se indican a continuación \(`_MCW_EM`, `_EM_INVALID`, etc.\) como argumentos para estas funciones, en lugar de proporcionar los valores hexadecimales explícitamente.  
  
 Las plataformas derivadas de Intel \(x86\) admiten los valores de entrada y salida desnormalizados en el hardware.  El comportamiento de x86 consiste en conservar los valores desnormalizados.  La plataforma ARM y las plataformas de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] compatibles con SSE2 permiten que los operandos y resultados desnormalizados se vacíen, es decir, que se conviertan en cero.  Las funciones `_controlfp` y `_control87` proporcionan una máscara para cambiar este comportamiento.  En el siguiente ejemplo se muestra la forma de usar esta máscara.  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 En las plataformas ARM, las funciones `_control87` y `_controlfp` se aplican al registro de FPSCR.  En arquitecturas de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], solo se ve afectada la palabra de control de SSE2 almacenada en el registro de MXCSR.  En plataformas Intel \(x86\), `_control87` y `_controlfp` afectan a las palabras de control de x87 y SSE2, si existen.  La función `__control87_2` permite controlar las unidades de punto flotantes de x87 y SSE2 juntas o por separado.  Si desea que se vean afectadas las dos unidades, pase las direcciones de dos enteros a `x86_cw` y `sse2_cw`.  Si desea que solo se vea afectada una unidad, pase una dirección para ese parámetro y pase 0 para el otro.  Si se pasa 0 para uno de estos parámetros, la función no tiene ningún efecto en esa unidad de punto flotante.  Esta funcionalidad podría ser útil en situaciones en la que parte del código usa la unidad de punto flotante x87 y otra parte usa la unidad de punto flotante SSE2.  Si usa `__control87_2` en una parte de un programa y establece valores distintos para las palabras de control de punto flotante, y a continuación usa `_control87` o `_controlfp` para manipular todavía más la palabra de control, quizás `_control87` y `_controlfp` no puedan devolver una sola palabra de control para representar el estado de las dos unidades de punto flotante.  En ese caso, estas funciones establecen el indicador `EM_AMBIGUOUS` en el valor entero devuelto para indicar que hay una incoherencia entre las dos palabras de control.  Se trata de una forma de advertir que la palabra de control devuelta podría no representar con precisión el estado de las dos palabras de control de punto flotante.  
  
 En las arquitecturas de ARM y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] no se puede cambiar el modo de infinito ni la precisión de punto flotante.  Si la máscara de control de precisión se usa en la plataforma [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], la función genera una aserción y se invoca el controlador de parámetro no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
> [!NOTE]
>  `__control87_2` no se admite en las arquitecturas ARM ni [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].  Si usa `__control87_2` y compila el programa para las arquitecturas de ARM o de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], el compilador genera un error.  
  
 Estas funciones se omiten si se usa [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) o `/clr:pure` para compilar, porque Common Language Runtime \(CLR\) solo admite la precisión de punto flotante predeterminada.  
  
 **Valores hexadecimales**  
  
 En el caso de la máscara `_MCW_EM`, si se borra la máscara se establece la excepción, con lo que se permite la excepción de hardware. Si se establece la máscara, se oculta la excepción.  Si se produce una constante `_EM_UNDERFLOW` o `_EM_OVERFLOW`, no se genera ninguna excepción de hardware hasta que se ejecute la instrucción de punto flotante siguiente.  Para generar una excepción de hardware inmediatamente después de `_EM_UNDERFLOW` o `_EM_OVERFLOW`, llame a la instrucción de MASM `FWAIT`.  
  
|Máscara|Valor hexadecimal|Constante|Valor hexadecimal|  
|-------------|-----------------------|---------------|-----------------------|  
|`_MCW_DN` \(control desnormalizado\)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` \(máscara de excepción de interrupción\)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` \(control de infinito\)<br /><br /> \(No se admite en las plataformas ARM o ni[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].\)|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` \(control de redondeo\)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` \(control de precisión\)<br /><br /> \(No se admite en las plataformas ARM o ni[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].\)|0x00030000|`_PC_24` \(24 bits\)<br /><br /> `_PC_53` \(53 bits\)<br /><br /> `_PC_64` \(64 bits\)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_control87`, `_controlfp`, `_control87_2`|\<float.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_cntrl87.c  
// processor: x86  
// This program uses __control87_2 to output the x87 control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
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
  
## Resultados  
  
```  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_clear87, \_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)