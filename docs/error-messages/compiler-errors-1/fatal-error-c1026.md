---
title: Error irrecuperable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204658"
---
# <a name="fatal-error-c1026"></a>Error irrecuperable C1026

desbordamiento de la pila del analizador, programa demasiado complejo

El espacio necesario para analizar el programa provocó un desbordamiento de pila del compilador.

Reducir la complejidad de las expresiones:

- Reducir el anidamiento en las instrucciones `for` y `switch`. Coloque instrucciones anidadas más profundamente en funciones independientes.

- División de expresiones largas que incluyen operadores de comas o llamadas de función.
