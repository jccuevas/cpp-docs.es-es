---
title: Platform::Collections::VectorViewIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363694"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator (Clase)

Proporciona un iterador de biblioteca de`IVectorView` plantillas estándar para los objetos derivados de la interfaz de Windows en tiempo de ejecución.

`ViewVectorIterator` es un iterador de proxy que almacena los elementos de tipo `VectorProxy<T>`. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El typename de la clase de plantilla VectorViewIterator.

### <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|
|`iterator_category`|La categoría de un iterador de acceso aleatorio (::std::random_access_iterator_tag).|
|`pointer`|Un puntero a un tipo interno necesario para la implementación de VectorViewIterator.|
|`reference`|Una referencia a un tipo interno necesario para la implementación de VectorViewIterator.|
|`value_type`|El typename `T` .|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializa una nueva instancia de la clase VectorViewIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorViewIterator::operador- Operador](#operator-minus)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|
|[VectorViewIterator::operator-- Operador](#operator-decrement)|Disminuye el objeto VectorViewIterator actual.|
|[Operador VectorViewIterator::operator!](#operator-inequality)|Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.|
|[Operador VectorViewIterator::operator*](#operator-dereference)|Recupera una referencia al elemento especificado por el objeto VectorViewIterator actual.|
|[VectorViewIterator::operator\[\]](#operator-at)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorViewIterator actual.|
|[VectorViewIterator::operador+ Operador](#operator-plus)|Devuelve un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator especificado.|
|[VectorViewIterator::operador++ Operador](#operator-increment)|Incrementa el objeto VectorViewIterator actual.|
|[Operador VectorViewIterator::operator+](#operator-plus-equals)|Incrementa el VectorViewIterator actual según el desplazamiento especificado.|
|[VectorViewIterator::operador< Operador](#operator-less-than)|Indica si el objeto VectorViewIterator actual es menor que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operador\<- Operador](#operator-less-than-or-equals)|Indica si el objeto VectorViewIterator actual es menor o igual que un objeto VectorViewIterator especificado.|
|[Operador VectorViewIterator::operador--](#operator-minus-assign)|Disminuye el objeto VectorViewIterator actual según el desplazamiento especificado.|
|[VectorViewIterator::operador - Operador](#operator-equality)|Indica si el objeto VectorViewIterator actual es igual que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator> (Operador)](#operator-greater-than)|Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operador-operador > Operador](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto VectorViewIterator actual.|
|[VectorViewIterator::operador>- Operador](#operator-greater-than-or-equals)|Indica si el objeto VectorViewIterator actual es mayor o igual que un objeto VectorViewIterator especificado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VectorViewIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator::operador-&gt; Operador

Recupera la dirección del elemento al que hace referencia el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Valor del elemento al que hace referencia el objeto VectorViewIterator actual.

El tipo del valor devuelto es un tipo interno no especificado que se requiere para la implementación de este operador.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator::operator-- Operador

Disminuye el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis disminuye y devuelve después el objeto VectorViewIterator actual. La segunda sintaxis devuelve una copia del objeto VectorViewIterator actual y disminuye después el objeto VectorViewIterator actual.

### <a name="remarks"></a>Observaciones

La primera sintaxis de VectorViewIterator disminuye previamente el objeto VectorViewIterator actual.

La segunda sintaxis disminuye posteriormente el objeto VectorViewIterator actual. El tipo `int` de la segunda sintaxis indica una operación de decremento posterior, no un operando entero real.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator::operador\* Operador

Recupera una referencia al elemento especificado por el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El elemento especificado por el objeto VectorViewIterator actual.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator::operador - Operador

Indica si el objeto VectorViewIterator actual es igual que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**true** si `VectorViewIterator` la corriente es igual a *otra*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator::operador&gt; Operador

Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**true** si el VectorViewIterator actual es mayor que *otros*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator::operador&gt;- Operador

Indica si la `VectorViewIterator` corriente es mayor o `VectorViewIterator`igual que la especificada.

### <a name="syntax"></a>Sintaxis

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**true** si `VectorViewIterator` la corriente es mayor o igual que *otra*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator::operador++ Operador

Incrementa el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis incrementa y devuelve después el objeto VectorViewIterator actual. La segunda sintaxis devuelve una copia del objeto VectorViewIterator actual e incrementa después el objeto VectorViewIterator actual.

### <a name="remarks"></a>Observaciones

La primera sintaxis de VectorViewIterator incrementa previamente el objeto VectorViewIterator actual.

La segunda sintaxis incrementa posteriormente el objeto VectorViewIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>Operador VectorViewIterator::operator!

Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**true** si `VectorViewIterator` la corriente no es igual a *otra*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator::operador&lt; Operador

Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto `VectorIterator`.

### <a name="return-value"></a>Valor devuelto

**true** si `VectorIterator` la corriente es menor que *otra*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator::operador&lt;- Operador

Indica si la `VectorIterator` corriente es menor o `VectorIterator`igual que una .

### <a name="syntax"></a>Sintaxis

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Otro objeto `VectorIterator`.

### <a name="return-value"></a>Valor devuelto

**true** si `VectorIterator` la corriente es menor o igual que *otra*; de lo contrario, **false**.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator::operador- Operador

Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Número de elementos.

*Otro*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

La sintaxis del primer operador devuelve un objeto VectorViewIterator que tiene `n` elementos menos que el objeto VectorViewIterator actual. La segunda sintaxis del operador devuelve el número de elementos que hay entre el objeto actual y `other` VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>Operador VectorViewIterator::operator+

Incrementa el VectorViewIterator actual según el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorViewIterator actualizado.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator::operador+ Operador

Devuelve un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
En la segunda sintaxis, el typename del objeto VectorViewIterator.

*N*<br/>
Desplazamiento entero.

*Ⅰ*<br/>
En la segunda sintaxis, un objeto VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

En la primera sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator actual.

En la segunda sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>Operador VectorViewIterator::operador--

Disminuye el VectorIterator actual según el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorIterator actualizado.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator::operator\[\]

Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parámetros

*N*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

El elemento que se desplaza `n` elementos del objeto VectorViewIterator actual.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator::VectorViewIterator Constructor

Inicializa una nueva instancia de la clase VectorViewIterator.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parámetros

*Ⅴ*<br/>
Un IVectorView\<T> objeto.

### <a name="remarks"></a>Observaciones

El primer ejemplo de sintaxis es el constructor predeterminado. El segundo ejemplo de sintaxis es un constructor explícito que se\<utiliza para construir un VectorViewIterator a partir de un IVectorView T> objeto.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)
