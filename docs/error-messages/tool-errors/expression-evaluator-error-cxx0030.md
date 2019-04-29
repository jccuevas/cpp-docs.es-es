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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359805"
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030

expresión no evaluable

Evaluador de expresiones del depurador no pudo obtener un valor para la expresión mientras escribe. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (desreferencia un puntero null es un ejemplo). Windows no permiten el acceso a la memoria que está fuera del espacio de direcciones del programa.

Es posible que desee escribir la expresión con paréntesis para controlar el orden de evaluación.

Este error es idéntico a CAN0030.