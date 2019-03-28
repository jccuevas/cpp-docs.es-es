---
title: Platform::Collections::VectorViewIterator (Clase)
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 0de4ffb8e72c21490f07ae164aa23ffcd524c2b8
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565667"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator (Clase)

Proporciona un iterador de la biblioteca de plantillas estándar para los objetos derivados de Windows Runtime`IVectorView` interfaz.

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

|Name|Descripción|
|----------|-----------------|
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|
|`iterator_category`|La categoría de un iterador de acceso aleatorio (::std::random_access_iterator_tag).|
|`pointer`|Un puntero a un tipo interno necesario para la implementación de VectorViewIterator.|
|`reference`|Una referencia a un tipo interno necesario para la implementación de VectorViewIterator.|
|`value_type`|El typename `T` .|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializa una nueva instancia de la clase VectorViewIterator.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[VectorViewIterator::operator[] (Operador)](#operator-minus)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|
|[VectorViewIterator::operator[] (Operador)](#operator-decrement)|Disminuye el objeto VectorViewIterator actual.|
|[VectorViewIterator::operator!= (Operador)](#operator-inequality)|Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator[] (Operador)](#operator-dereference)|Recupera una referencia al elemento especificado por el objeto VectorViewIterator actual.|
|[VectorViewIterator::operator\[\]](#operator-at)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorViewIterator actual.|
|[VectorViewIterator::operator+ (Operador)](#operator-plus)|Devuelve un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator++ (Operador)](#operator-increment)|Incrementa el objeto VectorViewIterator actual.|
|[VectorViewIterator::operator+= (Operador)](#operator-plus-equals)|Incrementa el VectorViewIterator actual según el desplazamiento especificado.|
|[VectorViewIterator::operator< (Operador)](#operator-less-than)|Indica si el objeto VectorViewIterator actual es menor que un objeto VectorViewIterator especificado.|
|[Vectorviewiterator:: operator\<= (operador)](#operator-less-than-or-equals)|Indica si el objeto VectorViewIterator actual es menor o igual que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator-= (Operador)](#operator-minus-assign)|Disminuye el objeto VectorViewIterator actual según el desplazamiento especificado.|
|[VectorViewIterator::operator== (Operador)](#operator-equality)|Indica si el objeto VectorViewIterator actual es igual que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator> (Operador)](#operator-greater-than)|Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.|
|[VectorViewIterator::operator-> (Operador)](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto VectorViewIterator actual.|
|[VectorViewIterator::operator>= (Operador)](#operator-greater-than-or-equals)|Indica si el objeto VectorViewIterator actual es mayor o igual que un objeto VectorViewIterator especificado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VectorViewIterator`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Platform::Collections

## <a name="operator-arrow"></a>  VectorViewIterator::operator-&gt; Operator

Recupera la dirección del elemento al que hace referencia el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Valor del elemento al que hace referencia el objeto VectorViewIterator actual.

El tipo del valor devuelto es un tipo interno no especificado que se requiere para la implementación de este operador.

## <a name="operator-decrement"></a>  VectorViewIterator::operator-- Operator

Disminuye el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis disminuye y devuelve después el objeto VectorViewIterator actual. La segunda sintaxis devuelve una copia del objeto VectorViewIterator actual y disminuye después el objeto VectorViewIterator actual.

### <a name="remarks"></a>Comentarios

La primera sintaxis de VectorViewIterator disminuye previamente el objeto VectorViewIterator actual.

La segunda sintaxis disminuye posteriormente el objeto VectorViewIterator actual. El tipo `int` de la segunda sintaxis indica una operación de decremento posterior, no un operando entero real.

## <a name="operator-dereference"></a>  VectorViewIterator::operator\* Operator

Recupera una referencia al elemento especificado por el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El elemento especificado por el objeto VectorViewIterator actual.

## <a name="operator-equality"></a>  VectorViewIterator::operator== Operator

Indica si el objeto VectorViewIterator actual es igual que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**True** si actual `VectorViewIterator` es igual a *otros*; en caso contrario, **false**.

## <a name="operator-greater-than"></a>  VectorViewIterator::operator&gt; Operator

Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto VectorViewIterator actual es mayor que *otros*; en caso contrario, **false**.

## <a name="operator-greater-than-or-equals"></a>  VectorViewIterator::operator&gt;= Operator

Indica si el actual `VectorViewIterator` es mayor o igual que el especificado `VectorViewIterator`.

### <a name="syntax"></a>Sintaxis

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**True** si actual `VectorViewIterator` es mayor o igual a *otros*; en caso contrario, **false**.

## <a name="operator-increment"></a>  VectorViewIterator::operator++ Operator

Incrementa el objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Valor devuelto

La primera sintaxis incrementa y devuelve después el objeto VectorViewIterator actual. La segunda sintaxis devuelve una copia del objeto VectorViewIterator actual e incrementa después el objeto VectorViewIterator actual.

### <a name="remarks"></a>Comentarios

La primera sintaxis de VectorViewIterator incrementa previamente el objeto VectorViewIterator actual.

La segunda sintaxis incrementa posteriormente el objeto VectorViewIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.

## <a name="operator-inequality"></a>  VectorViewIterator::operator!= Operator

Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

**True** si actual `VectorViewIterator` no es igual a *otros*; en caso contrario, **false**.

## <a name="operator-less-than"></a>  VectorViewIterator::operator&lt; Operator

Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.

### <a name="syntax"></a>Sintaxis

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro `VectorIterator`.

### <a name="return-value"></a>Valor devuelto

**True** si actual `VectorIterator` es menor que *otros*; en caso contrario, **false**.

## <a name="operator-less-than-or-equals"></a>  VectorViewIterator::operator&lt;= Operator

Indica si el actual `VectorIterator` es menor o igual que un determinado `VectorIterator`.

### <a name="syntax"></a>Sintaxis

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Otro `VectorIterator`.

### <a name="return-value"></a>Valor devuelto

**True** si actual `VectorIterator` es menor o igual que *otros*; en caso contrario, **false**.

## <a name="operator-minus"></a>  VectorViewIterator::operator- Operator

Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parámetros

*n*<br/>
Número de elementos.

*other*<br/>
Otro VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

La sintaxis del primer operador devuelve un objeto VectorViewIterator que tiene `n` elementos menos que el objeto VectorViewIterator actual. La segunda sintaxis del operador devuelve el número de elementos que hay entre el objeto actual y `other` VectorViewIterator.

## <a name="operator-plus-equals"></a>  VectorViewIterator::operator+= Operator

Incrementa el VectorViewIterator actual según el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*n*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorViewIterator actualizado.

## <a name="operator-plus"></a>  VectorViewIterator::operator+ Operator

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

*n*<br/>
Desplazamiento entero.

*i*<br/>
En la segunda sintaxis, un objeto VectorViewIterator.

### <a name="return-value"></a>Valor devuelto

En la primera sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator actual.

En la segunda sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.

## <a name="operator-minus-assign"></a>  VectorViewIterator::operator-= Operator

Disminuye el VectorIterator actual según el desplazamiento especificado.

### <a name="syntax"></a>Sintaxis

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parámetros

*n*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

VectorIterator actualizado.

## <a name="operator-at"></a>  VectorViewIterator::operator\[\]

Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorViewIterator actual.

### <a name="syntax"></a>Sintaxis

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parámetros

*n*<br/>
Desplazamiento entero.

### <a name="return-value"></a>Valor devuelto

El elemento que se desplaza `n` elementos del objeto VectorViewIterator actual.

## <a name="ctor"></a>  VectorViewIterator::VectorViewIterator Constructor

Inicializa una nueva instancia de la clase VectorViewIterator.

### <a name="syntax"></a>Sintaxis

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parámetros

*v*<br/>
Una interfaz IVectorView\<T > objeto.

### <a name="remarks"></a>Comentarios

El primer ejemplo de sintaxis es el constructor predeterminado. El segundo ejemplo de sintaxis es un constructor explícito que se usa para construir un VectorViewIterator a partir de una interfaz IVectorView\<T > objeto.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)
