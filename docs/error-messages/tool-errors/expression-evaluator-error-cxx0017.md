---
title: Error del evaluador de expresiones CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602542"
---
# <a name="expression-evaluator-error-cxx0017"></a>Error del evaluador de expresiones CXX0017

no se encontró el símbolo

No se encontró un símbolo especificado en una expresión.

Una posible causa de este error es un error de coincidencia de mayúsculas en el nombre del símbolo. Dado que C y C++ son lenguajes entre mayúsculas y minúsculas, debe proporcionarse un nombre de símbolo en el caso exacto en el que se define en el origen.

Este error puede producirse al intentar convertir el tipo de una variable con el fin de ver la variable durante la depuración. El `typedef` declara un nuevo nombre para un tipo, pero no define un nuevo tipo. La conversión de tipo ha intentado en el depurador requiere que el nombre de un tipo definido.

Este error es idéntico a CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Asegúrese de que el símbolo se ha declarado en el punto en el programa donde se va a utilizar.

1. Utilice un nombre de tipo real para convertir variables en el depurador, en lugar de un `typedef`-definido por el nombre.