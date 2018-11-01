---
title: Error del evaluador de expresiones CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500352"
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030

expresión no evaluable

Evaluador de expresiones del depurador no pudo obtener un valor para la expresión mientras escribe. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (desreferencia un puntero null es un ejemplo). Windows no permiten el acceso a la memoria que está fuera del espacio de direcciones del programa.

Es posible que desee escribir la expresión con paréntesis para controlar el orden de evaluación.

Este error es idéntico a CAN0030.