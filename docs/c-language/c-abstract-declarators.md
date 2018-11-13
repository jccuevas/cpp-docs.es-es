---
title: Declaraciones abstractas de C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 5dc58b71c8b2032342b6604112673086dc94649b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429827"
---
# <a name="c-abstract-declarators"></a>Declaraciones abstractas de C

Un declarador abstracto es un declarador sin identificador, que consta de uno o más modificadores de puntero, matriz o función. El modificador de puntero (<strong>\*</strong>) precede siempre al identificador en un declarador; los modificadores de matriz (**[ ]**) y los modificadores de función ( **( )** ) van detrás del identificador. Teniendo esto en cuenta, puede determinar dónde aparecería el identificador en un declarador abstracto e interpretar el declarador en consecuencia. Vea [Interpretación de declaradores más complejos](../c-language/interpreting-more-complex-declarators.md) para obtener información adicional y ejemplos de declaradores complejos. Normalmente, puede usarse `typedef` para simplificar los declaradores. Vea [Declaraciones typedef](../c-language/typedef-declarations.md).

Los declaradores abstractos pueden ser complejos. Los paréntesis en un declarador abstracto complejo especifican una interpretación concreta, del mismo modo que en los declaradores complejos de las declaraciones.

En estos ejemplos se muestran declaradores abstractos:

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
>  El declarador abstracto que consta de un conjunto de paréntesis vacíos, **( )**, no se permite porque es ambiguo. No se puede determinar si el identificador implícito va dentro de los paréntesis (en cuyo caso será un tipo sin modificar) o delante de los paréntesis (en cuyo caso será un tipo de función).

## <a name="see-also"></a>Vea también

[Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)