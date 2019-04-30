---
title: Error del evaluador de expresiones CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 93f8389ed3959d5747e46c1234fd8d2eae0f1ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359844"
---
# <a name="expression-evaluator-error-cxx0024"></a>Error del evaluador de expresiones CXX0024

la operación necesita valor l

Se especificó una expresión que no se evalúa como un valor l para una operación que requiere un valor l.

Un valor l (denominado así porque aparece en el lado izquierdo de una instrucción de asignación) es una expresión que hace referencia a una ubicación de memoria.

Por ejemplo, `buffer[count]` es un valor l válido porque señala a una ubicación de memoria específica. La comparación lógica `zed != 0` no es un valor l válido porque se evalúa como TRUE o FALSE, no a una dirección de memoria.

Este error es idéntico a CAN0024.