---
title: Operadores de conversión | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 341812299d8cf95e351a087e9957dc0425cb25b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075948"
---
# <a name="casting-operators"></a>Operadores de conversión

Hay varios operadores de conversión específicos del lenguaje C++. Estos operadores están diseñados para quitar una parte de la ambigüedad y riesgo inherentes a las conversiones antiguas del lenguaje C. Estos operadores son:

- [dynamic_cast](../cpp/dynamic-cast-operator.md) usada para la conversión de tipos polimórficos.

- [static_cast](../cpp/static-cast-operator.md) usada para la conversión de tipos no polimórficos.

- [const_cast](../cpp/const-cast-operator.md) usa para quitar el **const**, **volátil**, y **__unaligned** atributos.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) utilizado para la reinterpretación simple de bits.

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md) usa genera MSIL comprobable.

Use **const_cast** y **reinterpret_cast** como último recurso, ya que estos operadores plantean los mismos peligros que las conversiones antiguas. Sin embargo, siguen siendo necesarios para reemplazar completamente las conversiones antiguas.

## <a name="see-also"></a>Vea también

[Conversión](../cpp/casting.md)