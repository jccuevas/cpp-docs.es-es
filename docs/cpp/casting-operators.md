---
title: Operadores de conversión
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: eac274a0207be675b8d13532c3110c6e71bd55c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190110"
---
# <a name="casting-operators"></a>Operadores de conversión

Hay varios operadores de conversión específicos del lenguaje C++. Estos operadores están diseñados para quitar una parte de la ambigüedad y riesgo inherentes a las conversiones antiguas del lenguaje C. Estos operadores son:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) Se usa para la conversión de tipos polimórficos.

- [static_cast](../cpp/static-cast-operator.md) Se usa para la conversión de tipos no polimorfismo.

- [const_cast](../cpp/const-cast-operator.md) Se usa para quitar los atributos **const**, **volatile**y **__unaligned** .

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) Se utiliza para la reinterpretación simple de bits.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) Se usa C++en/CLI para producir MSIL comprobable.

Utilice **const_cast** y **reinterpret_cast** como último recurso, ya que estos operadores presentan los mismos peligros que las conversiones de estilo antiguas. Sin embargo, siguen siendo necesarios para reemplazar completamente las conversiones antiguas.

## <a name="see-also"></a>Consulte también

[Conversión](../cpp/casting.md)
