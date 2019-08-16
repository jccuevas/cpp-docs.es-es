---
title: cualquier clase
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268757"
---
# <a name="any-class"></a>cualquier clase

Los almacenes de una instancia de cualquier tipo que cumpla los requisitos de constructor, o bien tiene ningún valor, que es llamado el estado de la clase de cualquier objeto.

Se llama a la instancia almacenada el valor contenido. Dos estados son iguales si no tienen ningún valor, ya sea o tienen un valor y los valores contenidos son los mismos.

## <a name="syntax"></a>Sintaxis

```cpp
class any
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[any](#any)|Construye un objeto de tipo `any`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[emplace](#emplace)|Establece un valor de cualquier.|
|[has_value](#has_value)|Devuelve **true** si alguna tiene un valor.|
|[reset](#reset)|Restablece cualquier.|
|[swap](#swap)|Intercambia dos todos los objetos.|
|[type](#type)|Devuelve el tipo any.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_eq)|Reemplaza cualquier cualquiera con una copia de otro.|

## <a name="any"></a> Cualquier

Construye un objeto de tipo `any`. También incluye un destructor.

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a> emplace

Establece un valor de cualquier.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value

Devuelve **true** si alguna tiene un valor.

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> operator=

Reemplaza cualquier cualquiera con una copia de otro.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Cualquiera que se copia a cualquiera.

## <a name="reset"></a> Restablecer

Restablece cualquier.

```cpp
void reset() noexcept;
```

## <a name="swap"></a> intercambio

Intercambia dos todos los objetos.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> Tipo

Devuelve el tipo any.

```cpp
const type_info& type() const noexcept;
```
