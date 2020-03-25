---
title: Error del evaluador de expresiones CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185131"
---
# <a name="expression-evaluator-error-cxx0039"></a>Error del evaluador de expresiones CXX0039

el símbolo es ambiguo

El evaluador de expresiones de C no puede determinar qué instancia de un símbolo se va a utilizar en una expresión. El símbolo se produce más de una vez en el árbol de herencia.

Debe utilizar el operador de resolución de ámbito (`::`) para especificar explícitamente la instancia que se va a utilizar en la expresión.

Este error es idéntico a CAN0039.
