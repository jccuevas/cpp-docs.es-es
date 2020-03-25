---
title: Error del evaluador de expresiones CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195765"
---
# <a name="expression-evaluator-error-cxx0024"></a>Error del evaluador de expresiones CXX0024

la operación necesita valor l

Se especificó una expresión que no se evalúa como un valor l para una operación que requiere un valor l.

Un valor l (lo que se llama porque aparece en el lado izquierdo de una instrucción de asignación) es una expresión que hace referencia a una ubicación de memoria.

Por ejemplo, `buffer[count]` es un valor l válido porque apunta a una ubicación de memoria concreta. La comparación lógica `zed != 0` no es un valor l válido porque se evalúa como TRUE o FALSE, no con una dirección de memoria.

Este error es idéntico a CAN0024.
