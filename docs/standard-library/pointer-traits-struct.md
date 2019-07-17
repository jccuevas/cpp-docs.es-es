---
title: pointer_traits (Struct)
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
ms.openlocfilehash: 109e51ad9eba54f31b90da9b8b85bec105c7dce6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240429"
---
# <a name="pointertraits-struct"></a>pointer_traits (Struct)

Proporciona información que necesita un objeto de clase de plantilla `allocator_traits` para describir un asignador con el tipo de puntero `Ptr`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>Comentarios

Ptr puede ser un puntero sin formato de tipo `Ty *` o una clase con las siguientes propiedades.

```cpp
struct Ptr
{ // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj); // optional
};
```

## <a name="members"></a>Miembros

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`typedef T2 difference_type`|El tipo `T2` es `Ptr::difference_type` si ese tipo existe, de otro modo, `ptrdiff_t`. Si `Ptr` es un puntero sin formato, el tipo es `ptrdiff_t`.|
|`typedef T1 element_type`|El tipo `T1` es `Ptr::element_type` si ese tipo existe, de otro modo, `Ty`. Si `Ptr` es un puntero sin formato, el tipo es `Ty`.|
|`typedef Ptr pointer`|El tipo es `Ptr`.|

### <a name="structs"></a>Estructuras

|||
|-|-|
|`rebind`|Intenta convertir el tipo de puntero subyacente en un tipo especificado.|

### <a name="methods"></a>Métodos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[pointer_to](#pointer_to)|Convierte una referencia arbitraria en un objeto de clase `Ptr`.|

### <a name="pointer_to"></a> pointer_to

El método estático que devuelve `Ptr::pointer_to(obj)`, si esa función existe. De otro modo, no es posible convertir una referencia arbitraria en un objeto de clase `Ptr`. Si `Ptr` es un puntero sin formato, este método devuelve `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
