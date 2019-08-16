---
title: '&lt;lista&gt; funciones | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269027"
---
# <a name="ltlistgt-functions"></a>&lt;lista&gt; funciones

## <a name="swap"></a> intercambio

Intercambia los elementos de dos listas.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="remarks"></a>Comentarios

La función de plantilla ejecuta `left.swap(right)`.
