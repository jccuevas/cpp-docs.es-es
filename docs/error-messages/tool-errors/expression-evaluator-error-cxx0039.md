---
title: Error del evaluador de expresiones CXX0039 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5397426618c5dfcbaa6307105781ff2e6f2eb97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048336"
---
# <a name="expression-evaluator-error-cxx0039"></a>Error del evaluador de expresiones CXX0039

símbolo es ambiguo

El evaluador de expresiones de C no puede determinar qué instancia de un símbolo para usarlo en una expresión. El símbolo aparece más de una vez en el árbol de herencia.

Debe usar el operador de resolución de ámbito (`::`) para especificar la instancia para usar en la expresión de explícitamente.

Este error es idéntico a CAN0039.