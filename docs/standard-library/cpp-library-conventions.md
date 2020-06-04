---
title: Convenciones de la biblioteca de C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
ms.openlocfilehash: d92636a7ed63e09396ff68749560cde9d1f8639c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755712"
---
# <a name="c-library-conventions"></a>Convenciones de la biblioteca de C++

La biblioteca de C++ cumple prácticamente con las mismas convenciones que la biblioteca estándar de C, además de algunas más que se describen aquí.

Una implementación tiene cierta libertad en cómo declara los tipos y funciones de la biblioteca de C++:

- Los nombres de las funciones de la biblioteca estándar de C pueden tenerC++una vinculación extern "" o extern "C". Incluya el encabezado estándar de C adecuado, en lugar de declarar una entidad de biblioteca insertada.

- Un nombre de función miembro en una clase de biblioteca puede tener firmas de función adicionales además de las que aparecen en este documento. Puede asegurarse de que una llamada a función que se describe aquí se comporte según lo esperado, pero no puede tomar de forma fiable la dirección de una función miembro de biblioteca. (El tipo podría no ser el esperado).

- Una clase de biblioteca puede tener clases base (no virtuales) sin documentar. Una clase documentada según se deriva de otra clase puede, de hecho, derivarse de esa clase a través de otras clases sin documentar.

- Un tipo definido como sinónimo de algún tipo entero puede ser el mismo que uno de varios tipos enteros diferentes.

- Un tipo de máscara de bits puede implementarse como tipo entero o como enumeración. En cualquier caso, puede realizar operaciones bit a bit (como `AND` y `OR`) en valores del mismo tipo de máscara de bits. Los elementos `A` y `B` de un tipo de máscara de bits son valores distintos de cero, como `A` & `B` es cero.

- Una función de biblioteca que no tiene ninguna especificación de excepción puede producir una excepción arbitraria, a menos que su definición restrinja claramente esta posibilidad.

Por otro lado, hay algunas restricciones:

- La biblioteca estándar de C no usa macros de enmascaramiento. Solo se reservan firmas de función específicas, no los nombres de las propias funciones.

- Un nombre de función de biblioteca fuera de una clase no tendrá firmas de función adicionales sin documentar. Puede tomar esta dirección de forma fiable.

- Las clases base y funciones miembro descritas como virtuales son ciertamente virtuales, mientras que las que se describen como no virtuales son ciertamente no virtuales.

- Dos tipos definidos por la biblioteca de C++ son siempre diferentes a menos que este documento sugiera de forma explícita lo contrario.

- Las funciones que proporciona la biblioteca, incluidas las versiones predeterminadas de las funciones reemplazables, pueden producir *como máximo* esas excepciones que aparecen en cualquier especificación de excepción. Ningún destructor que proporcione la biblioteca produce excepciones. Las funciones de la biblioteca estándar de C pueden propagar una excepción, como cuando `qsort` llama a una función de comparación que produce una excepción, pero, de lo contrario, no producen excepciones.

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
