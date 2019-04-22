---
title: Operadores de conversión
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: e2ac8e9079b1d30dca077363bbb6cef35960902e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768957"
---
# <a name="casting-operators"></a>Operadores de conversión

Hay varios operadores de conversión específicos del lenguaje C++. Estos operadores están diseñados para quitar una parte de la ambigüedad y riesgo inherentes a las conversiones antiguas del lenguaje C. Estos operadores son:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) usada para la conversión de tipos polimórficos.

- [static_cast](../cpp/static-cast-operator.md) usada para la conversión de tipos no polimórficos.

- [const_cast](../cpp/const-cast-operator.md) usa para quitar el **const**, **volátil**, y **__unaligned** atributos.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) utilizado para la reinterpretación simple de bits.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) utilizados en C++/CLI genera MSIL comprobable.

Use **const_cast** y **reinterpret_cast** como último recurso, ya que estos operadores plantean los mismos peligros que las conversiones antiguas. Sin embargo, siguen siendo necesarios para reemplazar completamente las conversiones antiguas.

## <a name="see-also"></a>Vea también

[Conversión](../cpp/casting.md)