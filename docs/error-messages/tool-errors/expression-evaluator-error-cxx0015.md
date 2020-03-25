---
title: Error del evaluador de expresiones CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196071"
---
# <a name="expression-evaluator-error-cxx0015"></a>Error del evaluador de expresiones CXX0015

expresión demasiado compleja (desbordamiento de pila)

La expresión especificada era demasiado compleja o estaba demasiado anidada para la cantidad de almacenamiento disponible para el evaluador de expresiones de C.

El desbordamiento normalmente se produce debido a demasiados cálculos pendientes.

Reorganice la expresión para que cada componente de la expresión se pueda evaluar a medida que se encuentre, en lugar de tener que esperar a que se calculen otras partes de la expresión.

Divida la expresión en varios comandos.

Este error es idéntico a CAN0015.
