---
title: Error del evaluador de expresiones CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571787"
---
# <a name="expression-evaluator-error-cxx0065"></a>Error del evaluador de expresiones CXX0065

variable necesita el marco de pila

Una expresión contiene una variable que existe dentro del ámbito actual, pero no se ha creado aún.

Este error puede producirse cuando se ha ejecutado el prólogo de una función, pero todavía no configurar el marco de pila para la función, o si se ha ejecutado el código de salida para la función.

Recorrer el código de prólogo hasta que se ha configurado el marco de pila antes de evaluar la expresión.

Este error es idéntico a CAN0065.