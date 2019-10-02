---
title: Platform::Collections::Vector (Clase)
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: a70856be04a63cad1c700cb3cc52711dde410265
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816576"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector (Clase)

Representa una colección secuencial de objetos a los que se puede tener acceso individualmente por un índice. Implementa [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) para ayudar con el [enlace de datos](/windows/uwp/data-binding/data-binding-in-depth)XAML.

## <a name="syntax"></a>Sintaxis

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de los elementos contenidos en el objeto Vector.

*E*<br/>
Especifica un predicado binario para probar la igualdad con valores de tipo *T*. El valor predeterminado es `std::equal_to<T>`.

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

1. enteros

1. clase de interfaz ^

1. clase ref pública^

1. value struct

1. clase de enumeración pública

La clase **Vector** es la C++ implementación concreta de la interfaz [Windows:: Foundation:: Collections:: IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) .

Si intenta usar un tipo de **Vector** en un valor devuelto o parámetro público, se produce el error del compilador C3986. Puedes corregir el error si cambias el tipo del parámetro o del valor devuelto a [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Vector::Vector](#ctor)|Inicializa una nueva instancia de la clase Vector.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Vector::Append](#append)|Inserta el elemento especificado a continuación del último elemento en el objeto Vector actual.|
|[Vector::Clear](#clear)|Elimina todos los elementos del Vector actual.|
|[Vector::First](#first)|Devuelve un iterador que especifica el primer elemento del objeto Vector.|
|[Vector::GetAt](#getat)|Recupera el elemento del objeto Vector actual identificado por el índice especificado.|
|[Vector::GetMany](#getmany)|Recupera una secuencia de elementos del objeto Vector actual, empezando en el índice especificado.|
|[Vector::GetView](#getview)|Devuelve una vista de solo lectura de una clase Vector; es decir, [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md).|
|[Vector::IndexOf](#indexof)|Busca el elemento especificado en el objeto Vector actual y, si lo encuentra, devuelve el índice del elemento.|
|[Vector::InsertAt](#insertat)|Inserta el elemento especificado en el objeto Vector actual detrás del elemento identificado por el índice especificado.|
|[Vector::ReplaceAll](#replaceall)|Elimina los elementos del objeto Vector actual y después inserta los elementos de la matriz especificada.|
|[Vector::RemoveAt](#removeat)|Elimina el elemento identificado por el índice especificado del objeto Vector actual.|
|[Vector::RemoveAtEnd](#removeatend)|Elimina el elemento al final del objeto Vector actual.|
|[Vector::SetAt](#setat)|Asigna el valor especificado al elemento del objeto Vector actual identificado por el índice especificado.|
|[Vector::Size](#size)|Devuelve el número de elementos del objeto Vector actual.|

### <a name="events"></a>Events

|||
|-|-|
|Name|Descripción|
|evento [Windows:: Foundation:: Collection:: VectorChangedEventHandler @ no__t-1t > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Se produce cuando cambia el objeto Vector.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Vector`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Platform::Collections

## <a name="append"></a>Vector:: Append (método)

Inserta el elemento especificado a continuación del último elemento en el objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
El elemento que se va a insertar en el objeto Vector. El tipo de *elemento* se define mediante el TypeName *T* .

## <a name="clear"></a>Vector:: CLEAR (método)

Elimina todos los elementos del Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="first"></a>Vector:: First (método)

Devuelve un iterador que apunta al primer elemento del objeto Vector.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta al primer elemento del objeto Vector.

### <a name="remarks"></a>Comentarios

Una manera cómoda de contener el iterador devuelto por First () es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **auto** . Por ejemplo: `auto x = myVector->First();`. El iterador conoce la longitud de la colección.

Cuando necesite un par de iteradores para pasar a una función STL, use las funciones libres [Windows:: Foundation:: Collections:: Begin](../cppcx/begin-function.md) y [Windows:: Foundation:: Collections:: end](../cppcx/end-function.md) .

## <a name="getat"></a>Vector:: GetAt (método)

Recupera el elemento del objeto Vector actual identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

### <a name="return-value"></a>Valor devuelto

El elemento especificado por el parámetro de *Índice* . El tipo de elemento se define mediante el TypeName *T* .

## <a name="getmany"></a>Vector:: getmany ((método)

Recupera una secuencia de elementos del objeto Vector actual, empezando en el índice especificado, y los copia en la matriz asignada por el llamador.

### <a name="syntax"></a>Sintaxis

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parámetros

*startIndex*<br/>
Índice basado en cero del principio de los elementos que se van a recuperar.

*dest*<br/>
Matriz asignada por el llamador de elementos que comienzan en el elemento especificado por *startIndex* y terminan en el último elemento del vector.

### <a name="return-value"></a>Valor devuelto

Número de elementos recuperados.

### <a name="remarks"></a>Comentarios

Esta función no se ha diseñado para el uso en el código de cliente. Se usa internamente en la [función to_vector](../cppcx/to-vector-function.md) para habilitar la conversión eficaz de Platform:: Vector instancias en instancias de STD:: Vector.

## <a name="getview"></a>Vector:: GetView ((método)

Devuelve una vista de solo lectura de un objeto Vector; es decir, una interfaz IVectorView.

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Un objeto IVectorView.

## <a name="indexof"></a>Vector:: IndexOf (método)

Busca el elemento especificado en el objeto Vector actual y, si lo encuentra, devuelve el índice del elemento.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
El elemento que se va a buscar.

*index*<br/>
Índice de base cero del elemento si se encuentra el *valor* del parámetro; de lo contrario, es 0.

El parámetro de *Índice* es 0 si el elemento es el primer elemento del vector o no se encontró el elemento. Si el valor devuelto es **true**, se encontró el elemento y es el primer elemento; de lo contrario, no se encontró el elemento.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra el elemento especificado; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

IndexOf utiliza std::find_if para buscar el elemento. Por tanto, los tipos de elementos personalizados deben sobrecargar los operadores == y != para habilitar las comparaciones de igualdad que requiere find_if.

##  <a name="insertat"></a>Vector:: Insertat ((método)

Inserta el elemento especificado en el objeto Vector actual detrás del elemento identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

*item*<br/>
Elemento que se va a insertar en el vector después del elemento especificado por *index*. El tipo de *elemento* se define mediante el TypeName *T* .

## <a name="removeat"></a>Vector:: RemoveAt (método)

Elimina el elemento identificado por el índice especificado del objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

## <a name="removeatend"></a>Vector:: Removeatend ((método)

Elimina el elemento al final del objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>Vector:: ReplaceAll (método)

Elimina los elementos del objeto Vector actual y después inserta los elementos de la matriz especificada.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>Parámetros

*ARR*<br/>
Matriz de objetos cuyo tipo está definido por el TypeName *T* .

## <a name="setat"></a>Vector:: SetAt (método)

Asigna el valor especificado al elemento del objeto Vector actual identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

*item*<br/>
El valor que se va a asignar al elemento especificado. El tipo de *elemento* se define mediante el TypeName *T* .

## <a name="size"></a>Vector:: Size (método)

Devuelve el número de elementos del objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del Vector actual.

## <a name="ctor"></a>Vector:: Vector (constructor)

Inicializa una nueva instancia de la clase Vector.

### <a name="syntax"></a>Sintaxis

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Un [STD:: Array](../standard-library/array-class-stl.md) que se usará para inicializar el vector.

*ARR*<br/>
[Plataforma:: Array](../cppcx/platform-array-class.md) que se usará para inicializar el vector.

*InIt*<br/>
El tipo de una colección de objetos que se utiliza para inicializar el objeto Vector actual.

*il*<br/>
[STD:: initializer_list](../standard-library/initializer-list-class.md) de los objetos de tipo *T* que se usarán para inicializar el vector.

*N*<br/>
El número de elementos en una colección de objetos que se utiliza para inicializar el objeto Vector actual.

*size*<br/>
El número de elementos del objeto Vector.

*value*<br/>
Un valor que se utiliza para inicializar cada elemento en el objeto Vector actual.

*v*<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [STD:: Vector](../standard-library/vector-class.md) que se usa para inicializar el vector actual.

*ptr*<br/>
Puntero a un objeto `std::vector` que se usa para inicializar el objeto Vector actual.

*first*<br/>
El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de *primero* se pasa por medio del *reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de *último* se pasa por medio del *reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Vea también

[Colecciones (C++/CX)](collections-c-cx.md)<br/>
[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
