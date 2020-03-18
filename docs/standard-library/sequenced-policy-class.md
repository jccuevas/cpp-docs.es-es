---
title: sequenced_policy (clase)
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444918"
---
# <a name="sequenced_policy-class"></a>sequenced_policy (clase)

Se usa como un tipo único para eliminar la ambigüedad de la sobrecarga del algoritmo paralelo y requerir que la ejecución de un algoritmo paralelo no se ejecute en paralelo.

## <a name="syntax"></a>Sintaxis

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Observaciones

Durante la ejecución de un algoritmo paralelo con la Directiva de `execution::sequenced_policy`, si la invocación de una función de acceso de elemento sale a través de una excepción no detectada, se llamará a `terminate()`.
