---
title: Clase sequenced_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 63be7166b84fa452f53baf6b6de16831eb657a23
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269197"
---
# <a name="sequencedpolicy-class"></a>Clase sequenced_policy

Se utiliza como un tipo único para eliminar la ambigüedad de sobrecarga del algoritmo en paralelo y requieren que no se puede paralelizar la ejecución de un algoritmo paralelo.

## <a name="syntax"></a>Sintaxis

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Comentarios

Durante la ejecución de un algoritmo paralelo con la `execution::sequenced_policy` directiva, si sale de la invocación de una función de acceso de elemento a través de una excepción no detectada, `terminate()` se denominará.
