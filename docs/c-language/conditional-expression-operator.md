---
title: Operador de expresión condicional
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 9dc93a47d36af92fe370e3f56f504682d49bd1dd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150628"
---
# <a name="conditional-expression-operator"></a>Operador de expresión condicional

C tiene un operador ternario: el operador de expresión condicional (**? :**).

## <a name="syntax"></a>Sintaxis

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR expression*  **?**  *expression*  **:**  *conditional-expression*

El elemento *logical-OR-expression* debe ser de tipo entero, flotante o puntero. Se evalúa en términos de su equivalencia a 0. Un punto de secuencia sigue a *logical-OR-expression*. La evaluación de los operandos se produce de la manera siguiente:

- Si *logical-OR-expression* no es igual a 0, se evalúa *expression*. El resultado de evaluar la expresión lo determina el elemento *expression* no terminal. (Esto significa que *expression* solo se evalúa si *logical-OR-expression* es true).

- Si *logical-OR-expression* es igual a 0, se evalúa *conditional-expression*. El resultado de la expresión es el valor de *conditional-expression*. (Esto significa que *conditional-expression* solo se evalúa si *logical-OR-expression* es false).

Observe que se evalúa *expression* o *conditional-expression*, pero no ambas opciones.

El tipo de resultado de una operación condicional depende del tipo del operando de *expression* o *conditional-expression*, de la manera siguiente:

- Si *expression* o *conditional-expression* es de tipo entero o flotante (sus tipos pueden ser diferentes), el operador realiza las conversiones aritméticas habituales. El tipo del resultado es el tipo de los operandos después de la conversión.

- Si *expression* y *conditional-expression* tienen el mismo tipo de estructura, unión o puntero, el tipo del resultado es el mismo tipo de estructura, unión o puntero.

- Si ambos operandos son de tipo `void`, el resultado es de tipo `void`.

- Si el operando es un puntero a un objeto de cualquier tipo y el otro operando es un puntero a `void`, el puntero al objeto se convierte en un puntero a `void` y el resultado es un puntero a `void`.

- Si *expression* o *conditional-expression* es un puntero y el otro operando es una expresión constante con el valor 0, el tipo del resultado es el tipo de puntero.

En la comparación de punteros, cualquier calificador de tipo (**const** o `volatile`) en el tipo al que señala el puntero es insignificante, pero el tipo del resultado hereda los calificadores de ambos componentes del operador condicional.

## <a name="examples"></a>Ejemplos

En los ejemplos siguientes se muestran usos del operador condicional:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

En este ejemplo se asigna el valor absoluto de `i` a `j`. Si `i` es menor que 0, `-i` se asigna a `j`. Si `i` es mayor o igual que 0, `i` se asigna a `j`.

```
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

En este ejemplo, se declaran dos funciones, `f1` y `f2` y dos variables, `x` y `y`. Más adelante en el programa, si las dos variables tienen el mismo valor, se llama a la función `f1`. Si no, se llama a `f2`.

## <a name="see-also"></a>Vea también

[Operador condicional: ? :](../cpp/conditional-operator-q.md)
