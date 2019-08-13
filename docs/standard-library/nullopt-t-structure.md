---
title: Struct nullopt_t
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957041"
---
# <a name="nullopt_t-struct"></a>Struct nullopt_t

El `nullopt_t` tipo es un tipo único vacío que se usa para indicar que un objeto [opcional](optional-class.md) no contiene un valor.

La constante `nullopt` de tipo `nullopt_t` indica que `optional` un tipo tiene un estado no inicializado. Se puede usar para inicializar un `optional` objeto o compararlo con uno.

## <a name="syntax"></a>Sintaxis

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>Vea también

[\<> opcional](optional.md)\
[clase opcional](optional-class.md)
