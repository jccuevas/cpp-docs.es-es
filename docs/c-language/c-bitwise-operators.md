---
title: Operadores bit a bit de C
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168778"
---
# <a name="c-bitwise-operators"></a>Operadores bit a bit de C

Los operadores bit a bit realizan operaciones AND bit a bit ( **&** ), OR exclusivo bit a bit ( **^** ) y OR inclusivo bit a bit ( **&#124;** ).

## <a name="syntax"></a>Sintaxis

*And-Expression*: &nbsp;&nbsp;*la expresión de igualdad* &nbsp;&nbsp;*y-* Expression **&** *igualdad-Expression*

*exclusive-OR-expression*: &nbsp;&nbsp;*y-expression* &nbsp;&nbsp;expresión *and* - *OR-expression exclusiva-or-* **^** Expression

*inclusivo-or-Expression*: &nbsp;&nbsp;*Exclusive-or-* Expression &nbsp;&nbsp;la *expresión or* inclusiva or- *or-Expression* &#124;

Los operandos de los operadores bit a bit deben tener tipos enteros, pero sus tipos pueden ser diferentes. Estos operadores realizan las conversiones aritméticas habituales; el tipo del resultado es el tipo de los operandos después de la conversión.

A continuación se describen los operadores bit a bit de C:

|Operador|Descripción|
|--------------|-----------------|
|**&**|El operador AND bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si ambos bits son 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|
|**^**|El operador OR exclusivo bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si un bit es 0 y el otro bit es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|
|**&#124;**|El operador OR inclusivo bit a bit compara cada bit de su primer operando con el bit correspondiente de su segundo operando. Si uno de los dos bits es 1, el bit del resultado correspondiente se establece en 1. De lo contrario, el bit del resultado correspondiente se establece en 0.|

## <a name="examples"></a>Ejemplos

Estas declaraciones se utilizan para los tres ejemplos siguientes:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

El resultado asignado a `n` en este primer ejemplo es igual a `i` (0xAB00 hexadecimal).

```C
n = i | j;

n = i ^ j;
```

El operador OR inclusivo bit a bit del segundo ejemplo produce el valor 0xABCD (hexadecimal), mientras que el operador OR exclusivo bit a bit del tercer ejemplo genera 0xCD (hexadecimal).

**Específicos de Microsoft**

Los resultados de la operación bit a bit en enteros con signo se definen en la implementación según el estándar de ANSI C. Para el compilador de Microsoft C, las operaciones bit a bit en enteros con signo funcionan igual que las operaciones bit a bit en enteros sin signo. Por ejemplo, `-16 & 99` puede expresarse en formato binario como

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

El resultado de la operación AND bit a bit es 96 (decimal).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Operador AND bit a bit: &](../cpp/bitwise-and-operator-amp.md)<br/>
[Operador OR exclusivo bit a bit: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Operador OR inclusivo bit a bit: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
