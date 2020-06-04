---
title: default_delete (struct)
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269267"
---
# <a name="defaultdelete-struct"></a>default_delete (struct)

Objeto de función predefinido que realiza la operación de división (`operator/`) sobre sus argumentos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[default_delete](#default_delete)|Constructor para los objetos de tipo `default_delete`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator()](#op_paren)|Un operador de referencia para tener acceso a `default_delete`.|

## <a name="default_delete"></a> default_delete

Constructor para los objetos de tipo `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> operator()

Un operador de referencia para tener acceso a `default_delete`.

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Vea también

[\<memory>](../standard-library/memory.md)
