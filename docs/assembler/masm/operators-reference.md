---
title: Referencia de operadores de MASM
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: 5295307ad668b76e5ff39882ce2613f2042f914a
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395207"
---
# <a name="masm-operators-reference"></a>Referencia de operadores de MASM

## <a name="arithmetic"></a>Operadores aritméticos

||||
|-|-|-|
|[* (multiplicar)](operator-multiply.md)|[+ (sumar)](operator-add.md)|[-(restar o negar)](operator-subtract-2.md)|
|[. campo](operator-dot.md)|[/(dividir)](operator-subtract-1.md)|[&#91;&#93;ajustar](operator-brackets.md)|
|[MOD (resto)](operator-mod.md)|||

## <a name="control-flow"></a>Flujo de control

||||
|-|-|-|
|[\! (no lógico en tiempo de ejecución)](operator-logical-not-masm-run-time.md)|[\!= (tiempo de ejecución no igual)](operator-not-equal-masm.md)|[&#124;&#124;(OR lógico en tiempo de ejecución)](operator-logical-or.md)|
|[& & (and lógico en tiempo de ejecución)](operator-logical-and-masm-run-time.md)|[< (tiempo de ejecución menor que)](operator-less-than-masm-run-time.md)|[\<= (tiempo de ejecución menor o igual que)](operator-less-or-equal-masm-run-time.md)|
|[= = (tiempo de ejecución igual)](operator-equal-masm-run-time.md)|[> (tiempo de ejecución mayor que)](operator-greater-than-masm-run-time.md)|[> = (tiempo de ejecución mayor o igual que)](operator-greater-or-equal-masm-run-time.md)|
|[& (and bit a bit en tiempo de ejecución)](operator-bitwise-and.md)|||
|[PROCEDE? (Ejecutar prueba en tiempo de ejecución)](operator-carry-q.md)|[DESBORDAMIENTO? (prueba de desbordamiento en tiempo de ejecución)](operator-overflow-q.md)|[PARITY? (prueba de paridad en tiempo de ejecución)](operator-parity-q.md)|
|[SESIÓN? (prueba de firma en tiempo de ejecución)](operator-sign-q.md)|[NULO? (prueba de cero en tiempo de ejecución)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>And lógico

||||
|-|-|-|
|[AND (and bit a bit)](operator-and.md)|[NOT (not bit a bit)](operator-not.md)|[OR (OR bit a bit)](operator-or.md)|
|[SHL (bits de desplazamiento a la izquierda)](operator-shl.md)|[SHR (bits de desplazamiento a la derecha)](operator-shr.md)|[XOR (or exclusivo bit a bit)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[\! (literal de carácter)](operator-logical-not-masm.md)|[% (tratar como texto)](operator-percent.md)||
|[;; (tratar como comentario)](operator-semicolons.md)|[&lt; &gt; (tratar como un literal)](operator-literal.md)|[& & (valor del parámetro Substitute)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Varios

||||
|-|-|-|
|[' ' (tratar como cadena)](operator-single-quote.md)|["" (tratar como cadena)](operator-double-quote.md)||
|: (definición de etiqueta local)|:: (registrar segmento y desplazamiento)|:: (definición de etiqueta global)|
|[; (tratar como comentario)](operator-semicolon.md)|[DUP (declaración de repetición)](operator-dup.md)||

## <a name="record"></a>Record

|||
|-|-|
|[Máscara (obtener máscara de subred de registro o campo)](operator-mask.md)|[WIDTH (obtener registro o ancho de campo)](operator-width.md)|

## <a name="relational"></a>Relacional

||||
|-|-|-|
|[EQ (igual)](operator-eq.md)|[GE (mayor o igual que)](operator-ge.md)|[GT (mayor que)](operator-gt.md)|
|[LE (menor o igual que)](operator-le.md)|[LT (menor que)](operator-lt.md)|[NE (no es igual)](operator-ne.md)|

## <a name="segment"></a>sector

|||
|-|-|
|[: (invalidación de segmento)](operator-colon.md)|:: (registrar segmento y desplazamiento)|
|[IMAGEREL (desplazamiento relativo de la imagen)](operator-imagerel.md)|[LROFFSET (cargador de desplazamiento resuelto)](operator-lroffset.md)|
|[DESPLAZAMIENTO (desplazamiento relativo de segmento)](operator-offset.md)|[SECTIONREL (desplazamiento relativo de la sección)](operator-sectionrel.md)|
|[SEG (obtener segmento)](operator-seg.md)||

## <a name="type"></a>Tipo

||||
|-|-|-|
|[ALTO (8 bits superiores de 16 bits más bajos)](operator-high.md)|[HIGH32 (alto 32 bits de 64 bits)](operator-high32.md)|[HIGHWORD (16 bits superiores de los 32 bits más bajos)](operator-highword.md)|
|[LONGITUD (número de elementos de la matriz)](operator-length.md)|[LONGITUD (número de elementos de la matriz)](operator-lengthof.md)|[BAJO (8 bits inferiores)](operator-low.md)|
|[LOW32 (Low 32 bits)](operator-low32.md)|[LOWWORD (bajo 16 bits)](operator-lowword.md)|[OPATTR (obtener información de tipo de argumento)](operator-opattr.md)|
|[PTR (puntero a o como tipo)](operator-ptr.md)|[SHORT (marcar tipo corto de etiqueta)](operator-short.md)|[TAMAÑO (tamaño del tipo o variable)](operator-size.md)|
|[SIZEOF (tamaño del tipo o variable)](operator-sizeof.md)|[THIS (ubicación actual)](operator-this.md)|[TYPE (obtener tipo de expresión)](operator-type.md)|
|[. TYPE (obtener información de tipo de argumento)](operator-dot-type.md)|||

## <a name="see-also"></a>Vea también

[Referencia de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)<br/>
