---
title: Enumeraciones &lt;memory&gt;
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884082"
---
# <a name="ltmemorygt-enums"></a>Enumeraciones &lt;memory&gt;

## <a name="pointer_safety"></a>Enumeración pointer_safety

Enumeración de los posibles valores devueltos por `get_pointer_safety`.

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Observaciones

La **enumeración** con ámbito define los valores que puede devolver `get_pointer_safety()`:

`relaxed`: los punteros derivados de forma no segura (como punteros a objetos declarados o asignados) se tratan igual que los derivados de forma segura.

`preferred`: como antes, pero los punteros derivados de forma no segura no se deben desreferenciar.

`strict`: los punteros derivados de forma no segura se pueden tratar de manera diferente que los derivados de forma segura.
