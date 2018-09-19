---
title: Error del evaluador de expresiones CXX0030 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102819"
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030

expresión no evaluable

Evaluador de expresiones del depurador no pudo obtener un valor para la expresión mientras escribe. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (desreferencia un puntero null es un ejemplo). Windows no permiten el acceso a la memoria que está fuera del espacio de direcciones del programa.

Es posible que desee escribir la expresión con paréntesis para controlar el orden de evaluación.

Este error es idéntico a CAN0030.