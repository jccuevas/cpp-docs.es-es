---
title: operadores de&gt; de memory_resource de &lt;
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425476"
---
# <a name="ltmemory_resourcegt-operators"></a>operadores de&gt; de memory_resource de &lt;

## <a name="op_neq"></a>operador! =

Comprueba si el objeto de memory_resource en el lado izquierdo del operador no es igual que el objeto de memory_resource del lado derecho.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a>operador = =

Comprueba si el objeto de memory_resource en el lado izquierdo del operador es igual que el objeto de memory_resource del lado derecho.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
