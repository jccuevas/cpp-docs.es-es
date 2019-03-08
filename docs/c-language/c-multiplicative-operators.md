---
title: Operadores de multiplicación de C
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: fdf208ffba3e3d63d8672b84af8cf6168b34dc3f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147757"
---
# <a name="c-multiplicative-operators"></a>Operadores de multiplicación de C

Los operadores multiplicativos realizan operaciones de multiplicación (<strong>\*</strong>), división (**/**) y resto (**%**).

## <a name="syntax"></a>Sintaxis

*multiplicative-expression*: &nbsp;&nbsp;&nbsp;&nbsp;*cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* <strong>\*</strong> *cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* **/** *cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* **%** *cast-expression*

Los operandos del operador de resto (**%**) deben ser enteros. Los operadores de multiplicación (<strong>\*</strong>) y división (**/**) pueden tomar operandos de tipo entero o flotante; los tipos de los operandos pueden ser diferentes.

Los operadores multiplicativos realizan las conversiones aritméticas usuales en los operandos. El tipo del resultado es el tipo de los operandos después de la conversión.

> [!NOTE]
>  Como las conversiones realizadas por los operadores multiplicativos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación multiplicativa no se puede representar en el tipo de los operandos después de la conversión.

A continuación se describen los operadores multiplicativos de C:

|Operador|Descripción|
|--------------|-----------------|
|<strong>\*</strong>|El operador de multiplicación hace que se multipliquen sus dos operandos.|
|**/**|El operador de división hace que el primer operando se divida por el segundo. Si se dividen dos operandos enteros y el resultado no es un entero, se trunca según las reglas siguientes:<br/><br/>- El resultado de la división por 0 es indefinido según el estándar ANSI C. El compilador de C de Microsoft genera un error en tiempo de compilación o en tiempo de ejecución.<br/><br/>- Si ambos operandos son positivos o sin signo, el resultado se trunca hacia 0.<br/><br/>- Si alguno de los operandos es negativo, la implementación define si el resultado de la operación es el entero más grande menor o igual que el cociente algebraico o es el entero más pequeño mayor o igual que el cociente algebraico. (Vea la sección específica de Microsoft más adelante).|
|**%**|El resultado del operador de resto es el resto cuando el primer operando se divide por el segundo. Cuando la división es inexacta, el resultado viene determinado por las reglas siguientes:<br/><br/>- Si el operando derecho es cero, el resultado es indefinido.<br/><br/>- Si ambos operandos son positivos o sin signo, el resultado es positivo.<br/><br/>- Si algún operando es negativo y el resultado es inexacto, el resultado lo define la implementación. (Vea la sección específica de Microsoft más adelante).|

**Específicos de Microsoft**

En la división donde alguno de los operandos es negativo, la dirección del truncamiento es hacia 0.

Si alguna operación es negativa en la división con el operador de resto, el resultado tiene el mismo signo que el dividendo (el primer operando de la expresión).

**FIN de Específicos de Microsoft**

## <a name="examples"></a>Ejemplos

Las declaraciones que se muestran a continuación se utilizan en los ejemplos siguientes:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Esta instrucción utiliza el operador de multiplicación:

```
y = x * i;
```

En este caso, `x` se multiplica por `i` para asignar el valor 20,0. El resultado tiene el tipo **double**.

```
n = i / j;
```

En este ejemplo, 10 se divide por 3. El resultado se trunca hacia 0, produciendo el valor entero 3.

```
n = i % j;
```

Esta instrucción asigna `n` al resto entero, 1, cuando 10 se divide por 3.

**Específicos de Microsoft**

El signo del resto es igual que el signo del dividendo. Por ejemplo:

```
50 % -6 = 2
-50 % 6 = -2
```

En cada caso, `50` y `2` tienen el mismo signo.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Operadores de multiplicación y el operador de módulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)
