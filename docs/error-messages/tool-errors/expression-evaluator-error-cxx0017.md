---
title: Error del evaluador de expresiones CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196019"
---
# <a name="expression-evaluator-error-cxx0017"></a>Error del evaluador de expresiones CXX0017

no se encontró el símbolo

No se encontró un símbolo especificado en una expresión.

Una posible causa de este error es una falta de coincidencia de mayúsculas y minúsculas en el nombre del símbolo. Dado que C C++ y son lenguajes que distinguen mayúsculas de minúsculas, se debe proporcionar un nombre de símbolo en el caso exacto en el que se define en el origen.

Este error puede producirse al intentar convertir un objeto en una variable para ver la variable durante la depuración. El `typedef` declara un nuevo nombre para un tipo, pero no define un nuevo tipo. La conversión de tipos intentada en el depurador requiere el nombre de un tipo definido.

Este error es idéntico a CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Asegúrese de que el símbolo ya esté declarado en el punto del programa en el que se está usando.

1. Use un nombre de tipo real para convertir variables en el depurador, en lugar de un nombre definido por el `typedef`.
