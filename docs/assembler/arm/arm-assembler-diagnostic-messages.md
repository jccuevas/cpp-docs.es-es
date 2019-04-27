---
title: Mensajes de diagnóstico del ensamblador de ARM
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 867ef50065c6ed63a4da6d37523bd5a1f3cbadba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167848"
---
# <a name="arm-assembler-diagnostic-messages"></a>Mensajes de diagnóstico del ensamblador de ARM

El ensamblador de ARM Microsoft (*armasm*) emite errores y advertencias de diagnóstico cuando encuentra ellos. En este artículo se describe los mensajes más habituales.

## <a name="syntax"></a>Sintaxis

> <em>nombre de archivo</em>**(**<em>número de línea</em>**):** \[ **error**|**advertencia** ] **A**<em>número</em>**:** *mensaje*

## <a name="diagnostic-messages---errors"></a>Mensajes de diagnóstico: errores

> A2193: esta instrucción genera un comportamiento impredecible

La arquitectura ARM no puede garantizar qué ocurre cuando se ejecuta esta instrucción.  Para obtener más información acerca de las formas bien definidas de esta instrucción, consulte el [Manual de referencia de arquitectura ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: no se puede codificar la instrucción de 16 bits

La instrucción máquina especificada no se puede codificar como una instrucción de control de posición de 16 bits.  Especifique una instrucción de 32 bits o reorganizar el código para que la etiqueta de destino en el intervalo de una instrucción de 16 bits.

El ensamblador puede intentar codificar una bifurcación de 16 bits y se produce este error, aunque esté puedan codificarse con una rama de 32 bits. Puede resolver este problema mediante el uso de la `.W` especificador para marcar explícitamente la rama de 32 bits.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202: Sintaxis de instrucción de pre-UAL que no se admite en la región de control de posición

Código Thumb debe usar la sintaxis de Lenguaje unificado de ensamblador (UAL).  Ya no se acepta la sintaxis antigua

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513: Rotación debe ser par

En el modo ARM, hay una sintaxis alternativa para especificar las constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene girando el valor `<byte>` derecha `<rot>`.  Cuando se utiliza esta sintaxis, debe realizar el valor de `<rot>` incluso.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557: Número incorrecto de bytes para volver a escribir

En la estructura de NEÓN, cargar y almacenar instrucciones (`VLDn`, `VSTn`), hay una sintaxis alternativa para especificar la escritura diferida para el registro de base.  En lugar de colocar un signo de exclamación (!) después de la dirección, puede especificar un valor inmediato que indica el desplazamiento que se agregará al registro de base.  Si utiliza esta sintaxis, debe especificar el número exacto de bytes que se cargan o almacenan la instrucción.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Mensajes de diagnóstico - advertencias

> A4228: Alineación de área; supera el valor de alineación No garantizada de alineación

La alineación que se especifica en un `ALIGN` directiva es mayor que la alineación de la envolvente `AREA`.  Como resultado, el ensamblador no puede garantizar que el `ALIGN` se respetará la directiva.

Para solucionar este problema, puede especificar en el `AREA` directiva un `ALIGN` atributo que es igual o mayor que la alineación deseada.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508: Uso de esta constante girada es obsoleto

En el modo ARM, hay una sintaxis alternativa para especificar las constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene girando el valor `<byte>` derecha `<rot>`.  En algunos contextos, ARM ha dejado de usar de estas constantes giradas. En estos casos, use las opciones básicas `#<const>` sintaxis en su lugar.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509: Este formato de instrucción condicional está en desuso

Este formato de instrucción condicional ha dejado de utilizar ARM en la arquitectura de ARMv8. Se recomienda que cambie el código para usar las bifurcaciones condicionales. Para ver qué instrucciones condicionales siguen siendo compatibles, consulte el [Manual de referencia de arquitectura ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).

Esta advertencia no es emite cuando el **- oldit** se usa el modificador de línea de comandos.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>Vea también

[Referencia de la línea de comandos del ensamblador de ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Directivas del ensamblador de ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
