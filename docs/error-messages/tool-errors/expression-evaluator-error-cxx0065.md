---
title: Error del evaluador de expresiones CXX0065 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024169"
---
# <a name="expression-evaluator-error-cxx0065"></a>Error del evaluador de expresiones CXX0065

variable necesita el marco de pila

Una expresión contiene una variable que existe dentro del ámbito actual, pero no se ha creado aún.

Este error puede producirse cuando se ha ejecutado el prólogo de una función, pero todavía no configurar el marco de pila para la función, o si se ha ejecutado el código de salida para la función.

Recorrer el código de prólogo hasta que se ha configurado el marco de pila antes de evaluar la expresión.

Este error es idéntico a CAN0065.