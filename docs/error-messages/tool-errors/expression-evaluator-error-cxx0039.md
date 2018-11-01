---
title: Error del evaluador de expresiones CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463276"
---
# <a name="expression-evaluator-error-cxx0039"></a>Error del evaluador de expresiones CXX0039

símbolo es ambiguo

El evaluador de expresiones de C no puede determinar qué instancia de un símbolo para usarlo en una expresión. El símbolo aparece más de una vez en el árbol de herencia.

Debe usar el operador de resolución de ámbito (`::`) para especificar la instancia para usar en la expresión de explícitamente.

Este error es idéntico a CAN0039.