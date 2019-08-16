---
title: Enumeraciones &lt;memory&gt;
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243850"
---
# <a name="ltmemorygt-enums"></a>Enumeraciones &lt;memory&gt;

## <a name="pointer_safety"></a> Enumeración pointer_safety

Enumeración de los posibles valores devueltos por `get_pointer_safety`.

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Comentarios

El ámbito **enum** define los valores que pueden devolver `get_pointer_safety()`:

`relaxed`: los punteros derivados de forma no segura (como punteros a objetos declarados o asignados) se tratan igual que los derivados de forma segura.

`preferred`: como antes, pero los punteros derivados de forma no segura no se deben desreferenciar.

`strict`: los punteros derivados de forma no segura se pueden tratar de manera diferente que los derivados de forma segura.
