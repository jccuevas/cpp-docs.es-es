---
title: Clase parallel_unsequenced_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268787"
---
# <a name="parallelunsequencedpolicy-class"></a>Clase parallel_unsequenced_policy

Se utiliza como un tipo único para eliminar la ambigüedad de sobrecarga del algoritmo en paralelo e indicar que la ejecución de un algoritmo paralelo se puede ejecutar en paralelo y vectorizada.

## <a name="syntax"></a>Sintaxis

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>Comentarios

Durante la ejecución de un algoritmo paralelo con la `execution::parallel_unsequenced_policy` directiva, si sale de la invocación de una función de acceso de elemento a través de una excepción no detectada, `terminate()` se denominará.
