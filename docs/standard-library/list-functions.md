---
title: '&lt;lista de&gt; funciones | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425608"
---
# <a name="ltlistgt-functions"></a>&lt;lista de&gt; funciones

## <a name="swap"></a>pasar

Intercambia los elementos de dos listas.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `list`.

\ *derecha*
Objeto de tipo `list`.

### <a name="remarks"></a>Observaciones

La función de plantilla ejecuta `left.swap(right)`.
