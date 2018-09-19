---
title: Error del evaluador de expresiones CXX0017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136249"
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