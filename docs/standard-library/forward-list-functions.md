---
title: '&lt;forward_list&gt; (Funciones)'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240681"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; (Funciones)

## <a name="swap"></a> intercambio

Intercambia los elementos de dos listas de reenvío.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `forward_list`.

*Correcto*\
Objeto de tipo `forward_list`.

### <a name="remarks"></a>Comentarios

La función de plantilla ejecuta `left.swap(right)`.
