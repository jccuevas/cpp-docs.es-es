---
title: Referencia de operadores MASM
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: cb97c5dcb640b8d8592d842afd7dbb8cf9d0852c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210819"
---
# <a name="masm-operators-reference"></a>Referencia de operadores MASM

## <a name="arithmetic"></a>Operadores aritméticos

||||
|-|-|-|
|[* (multiplicar)](operator-multiply.md)|[+ (sumar)](operator-add.md)|[-(restar o negar)](operator-subtract-2.md)|
|[. (field)](operator-dot.md)|[/ (divide)](operator-subtract-1.md)|[&#91;&#93; (index)](operator-brackets.md)|
|[MOD (resto)](operator-mod.md)|||

## <a name="control-flow"></a>Flujo de control

||||
|-|-|-|
|[\! (not lógico en tiempo de ejecución)](operator-logical-not-masm-run-time.md)|[\!= (tiempo de ejecución no es igual)](operator-not-equal-masm.md)|[&#124;&#124;(en tiempo de ejecución lógico o)](operator-logical-or.md)|
|[& & (tiempo de ejecución lógico y)](operator-logical-and-masm-run-time.md)|[< (tiempo de ejecución menor que)](operator-less-than-masm-run-time.md)|[\<= (tiempo de ejecución menor o igual que)](operator-less-or-equal-masm-run-time.md)|
|[== (igual runtime)](operator-equal-masm-run-time.md)|[> (mayor que el runtime)](operator-greater-than-masm-run-time.md)|[> = (tiempo de ejecución mayor o igual)](operator-greater-or-equal-masm-run-time.md)|
|[& (tiempo de ejecución bit a bit y)](operator-bitwise-and.md)|||
|[¿CARRY? (prueba de transporte en tiempo de ejecución)](operator-carry-q.md)|[¿OVERFLOW? (comprobación de desbordamiento en tiempo de ejecución)](operator-overflow-q.md)|[¿PARIDAD? (comprobación de paridad en tiempo de ejecución)](operator-parity-q.md)|
|[¿INICIO DE SESIÓN? (en tiempo de ejecución de prueba de inicio de sesión)](operator-sign-q.md)|[¿CERO? (cero en tiempo de ejecución de prueba)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Lógico- and -Shift

||||
|-|-|-|
|[Y (bit a bit y)](operator-and.md)|[NO (not bit a bit)](operator-not.md)|[OR (bit a bit o)](operator-or.md)|
|[SHL (MAYÚS bits a la izquierda)](operator-shl.md)|[SHR (MAYÚS bits derecha)](operator-shr.md)|[XOR (exclusivo bit a bit o)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[\! (el carácter literal)](operator-logical-not-masm.md)|[% (tratado como texto)](operator-percent.md)||
|[;; (tratar como comentario)](operator-semicolons.md)|[&lt; &gt; (tratar como un literal)](operator-literal.md)|[& & (sustituya el valor de parámetro)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Varios

||||
|-|-|-|
|[' ' (tratar como cadena)](operator-single-quote.md)|["" (tratar como cadena)](operator-double-quote.md)||
|: (definición de etiqueta local)|:: (registrar el segmento y el desplazamiento)|:: (definición de etiqueta global)|
|[; (tratar como comentario)](operator-semicolon.md)|[DUP (declaración de repetición)](operator-dup.md)||

## <a name="record"></a>Record

|||
|-|-|
|[MÁSCARA (obtener el registro o campo de máscara de bits)](operator-mask.md)|[ANCHO (obtener el ancho de campo o de registro)](operator-width.md)|

## <a name="relational"></a>Relacional

||||
|-|-|-|
|[EQ (igual)](operator-eq.md)|[GE (mayor o igual que)](operator-ge.md)|[GT (mayor que)](operator-gt.md)|
|[LE (menor o igual)](operator-le.md)|[LT (menor que)](operator-lt.md)|[NE (no igual)](operator-ne.md)|

## <a name="segment"></a>Segmento

|||
|-|-|
|[: (invalidación de segmento)](operator-colon.md)|:: (registrar el segmento y el desplazamiento)|
|[IMAGEREL (desplazamiento relativo de imagen)](operator-imagerel.md)|[LROFFSET (el cargador resuelve desplazamiento)](operator-lroffset.md)|
|[DESPLAZAMIENTO (desplazamiento relativo del segmento)](operator-offset.md)|[SECTIONREL (desplazamiento relativo de sección)](operator-sectionrel.md)|
|[SEG (get segmento)](operator-seg.md)||

## <a name="type"></a>Tipo

||||
|-|-|-|
|[HIGH (altos 8 bits de 16 bits más bajas)](operator-high.md)|[HIGH32 (32 bits superiores de 64 bits)](operator-high32.md)|[HIGHWORD (16 bits superiores de 32 bits más bajas)](operator-highword.md)|
|[LONGITUD (número de elementos de matriz)](operator-length.md)|[LENGTHOF (número de elementos de matriz)](operator-lengthof.md)|[BAJA (8 bits inferiores)](operator-low.md)|
|[LOW32 (32 bits inferiores)](operator-low32.md)|[LOWWORD (16 bits inferiores)](operator-lowword.md)|[OPATTR (información de tipo de argumento get)](operator-opattr.md)|
|[PTR (puntero a o como tipo)](operator-ptr.md)|[SHORT (tipo de marca de etiqueta cortos)](operator-short.md)|[(Tamaño del tipo o variable)](operator-size.md)|
|[SIZEOF (tamaño de tipo o variable)](operator-sizeof.md)|[(Esta ubicación actual)](operator-this.md)|[TIPO (tipo de expresión de get)](operator-type.md)|
|[. TIPO (información de tipo de argumento get)](operator-dot-type.md)|||

## <a name="see-also"></a>Vea también

[Referencia de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)<br/>
