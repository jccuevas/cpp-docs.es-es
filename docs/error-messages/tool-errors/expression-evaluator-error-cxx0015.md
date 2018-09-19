---
title: Error del evaluador de expresiones CXX0015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050821"
---
# <a name="expression-evaluator-error-cxx0015"></a>Error del evaluador de expresiones CXX0015

expresión demasiado compleja (desbordamiento de pila)

La expresión especificado era demasiado compleja o demasiado anidada para almacenamiento disponible para el evaluador de expresiones de C.

Desbordamiento suele producirse debido a demasiados cálculos pendientes.

Reorganice la expresión para que pueda evaluarse cada componente de la expresión que se encuentre, en lugar de tener que esperar a otras partes de la expresión que se va a calcular.

Divida la expresión en varios comandos.

Este error es idéntico a CAN0015.