---
title: Platform::Collections::VectorIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354364"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator (Clase)

Proporciona un iterador de biblioteca de plantillas estándar para los objetos derivados de la interfaz IVector de Windows en tiempo de ejecución.

VectorIterator es un iterador de\<proxy que almacena elementos de tipo VectorProxy T>. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El typename de la clase de plantilla VectorIterator.

### <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|
|`iterator_category`|La categoría de un iterador de acceso aleatorio (::std::random_access_iterator_tag).|
|`pointer`|Un puntero a un tipo interno, Platform::Collections::Details::VectorProxy\<T>, que es necesario para la implementación de VectorIterator.|
|`reference`|Una referencia a un tipo interno, Platform::Collections::Details::VectorProxy\<T>, que es necesaria para la implementación de VectorIterator.|
|`value_type`|El typename `T` .|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|Inicializa una nueva instancia de la clase VectorIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorIterator::operador- Operador](#operator-minus)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|
|[VectorIterator::operador-- Operador](#operator-decrement)|Disminuye el objeto VectorIterator actual.|
|[VectorIterator::operador!- Operador](#operator-inequality)|Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.|
|[VectorIterator::operador* Operador](#operator-dereference)|Recupera una referencia al elemento especificado por el objeto VectorIterator actual.|
|[VectorIterator::operador\[\]](#operator-at)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorIterator actual.|
|[VectorIterator::operador+ Operador](#operator-plus)|Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.|
|[VectorIterator::operador++ Operador](#operator-increment)|Incrementa el objeto VectorIterator actual.|
|[Operador VectorIterator::operador+-](#operator-plus-assign)|Incrementa el objeto VectorIterator actual en el desplazamiento especificado.|
|[VectorIterator::operador< Operador](#operator-less-than)|Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.|
|[VectorIterator::operador\<- Operador](#operator-less-than-or-equals)|Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.|
|[Operador VectorIterator::operador--](#operator-minus-equals)|Disminuye el VectorIterator actual según el desplazamiento especificado.|
|[VectorIterator::operador- Operador](#operator-equality)|Indica si el objeto VectorIterator actual es igual que un objeto VectorIterator especificado.|
|[VectorIterator::operator> (Operador)](#operator-greater-than)|Indica si el objeto VectorIterator actual es mayor que un objeto VectorIterator especificado.|
|[VectorIterator::operador-operador > Operador](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto VectorIterator actual.|
|[VectorIterator:>de operador - Operador](#operator-greater-than-or-equals)|Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VectorIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorIterator::operador-&gt; Operador

Recupera la dirección del elemento al que hace referencia el objeto VectorIterator actual.

### <a name="syntax"></a>Sintaxis

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Valor del elemento al que hace referencia el objeto VectorIterator actual.

El tipo del valor devuelto es un tipo interno no especificado que se requiere para la implementación de este operador.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator::operador-- Operador

Disminuye el objeto VectorIterator actual.

### <a name="syntax"></a>Sintaxis

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis disminuye y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual y disminuye después el objeto VectorIterator actual.

### <a name="remarks"></a>Observaciones

La primera sintaxis de VectorIterator disminuye previamente el objeto VectorIterator actual.

La segunda sintaxis disminuye posteriormente el objeto VectorIterator actual. El tipo `int` de la segunda sintaxis indica una operación de decremento posterior, no un operando entero real.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>VectorIterator::operador\* Operador

Recupera la dirección del elemento especificado por el objeto VectorIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El elemento especificado por el objeto VectorIterator actual.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator::operador- Operador

Indica si el objeto VectorIterator actual es igual que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual es igual a *otro*; de lo contrario, **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorIterator::operador&gt; Operador

Indica si el objeto VectorIterator actual es mayor que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual es mayor que *otros*; de lo contrario, **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator::operador&gt;- Operador

Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual es mayor o igual que *otro*; de lo contrario, **false**.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>VectorIterator::operador++ Operador

Incrementa el objeto VectorIterator actual.

### <a name="syntax"></a>Sintaxis

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis incrementa y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual e incrementa después el objeto VectorIterator actual.

### <a name="remarks"></a>Observaciones

La primera sintaxis de VectorIterator incrementa previamente el objeto VectorIterator actual.

La segunda sintaxis incrementa posteriormente el objeto VectorIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>VectorIterator::operador!- Operador

Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual no es igual a *otro*; de lo contrario, **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorIterator::operador&lt; Operador

Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual es menor que *otros*; de lo contrario, **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator::operador&lt;- Operador

Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorIterator actual es menor o igual que *otro*; de lo contrario, **false**.

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>VectorIterator::operador- Operador

Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.

### <a name="syntax"></a>Sintaxis

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Número de elementos.

*Otro*<br/>
Otro objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

La sintaxis del primer operador devuelve un objeto VectorIterator que tiene `n` elementos menos que el objeto VectorIterator actual. La segunda sintaxis del operador devuelve el número de elementos que hay entre el objeto actual y `other` VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>Operador VectorIterator::operador+-

Incrementa el objeto VectorIterator actual en el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorIterator actualizado.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator::operador+ Operador

Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
En la segunda sintaxis, el typename del objeto VectorIterator.

*N*<br/>
Desplazamiento entero.

*Ⅰ*<br/>
En la segunda sintaxis, un objeto VectorIterator.

### <a name="return-value"></a>Valor devuelto

En la primera sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator actual.

En la segunda sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.

### <a name="remarks"></a>Observaciones

El ejemplo de la primera sintaxis

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>Operador VectorIterator::operador--

Disminuye el VectorIterator actual según el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorIterator actualizado.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator::operador\[\]

Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

El elemento que se desplaza `n` elementos del objeto VectorIterator actual.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>VectorIterator::VectorIterator Constructor

Inicializa una nueva instancia de la clase VectorIterator.

### <a name="syntax"></a>Sintaxis

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parámetros

*Ⅴ*<br/>
Un Objeto\<IVector T>.

### <a name="remarks"></a>Observaciones

El primer ejemplo de sintaxis es el constructor predeterminado. El segundo ejemplo de sintaxis es un constructor explícito que\<se utiliza para construir un VectorIterator a partir de un IVector T> objeto.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
