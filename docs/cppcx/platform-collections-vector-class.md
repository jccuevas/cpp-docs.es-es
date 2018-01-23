---
title: Clase Platform::Collections::vector | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
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
dev_langs: C++
helpviewer_keywords: Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f77962a6ba1eeb86abf4d91b3a308b4fb0d65ef
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector (Clase)

Representa una colección secuencial de objetos a los que se puede tener acceso individualmente por un índice.

## <a name="syntax"></a>Sintaxis

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>Parámetros

*T*  
Tipo de los elementos contenidos en el objeto Vector.

*E*  
Especifica un predicado binario para probar la igualdad con valores de tipo *T*. El valor predeterminado es `std::equal_to<T>`.

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

1. enteros

1. clase de interfaz ^

1. clase ref pública^

1. value struct

1. clase de enumeración pública

El **Vector** clase es la implementación concreta de C++ de la [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) interfaz.

Si intenta usar un **Vector** tipo en un valor devuelto público o un parámetro, C3986 se produce el error de compilador. Puede corregir el error cambiando el parámetro o devolver el tipo de valor a [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_). Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

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

### <a name="events"></a>Eventos

|||
|-|-|
|nombre|Descripción|
|evento [Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|Se produce cuando cambia el objeto Vector.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Vector`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="append"></a>Vector:: Append (método)

Inserta el elemento especificado a continuación del último elemento en el objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>Parámetros

*index*  
El elemento que se va a insertar en el objeto Vector. El tipo de *elemento* está definida por el *T* typename.

## <a name="clear"></a>Vector:: Clear (método)

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

Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myVector->First();`. El iterador conoce la longitud de la colección.

Si necesita un par de iteradores para pasar a una función STL, utilice las funciones libres [Collections:: begin](../cppcx/begin-function.md) y [Windows](../cppcx/end-function.md)

## <a name="getat"></a>Vector:: GetAt (método)

Recupera el elemento del objeto Vector actual identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>Parámetros

*index*  
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

### <a name="return-value"></a>Valor devuelto

El elemento especificado por la *índice* parámetro. El tipo de elemento se define mediante la *T* typename.

## <a name="getmany"></a>Vector:: getmany (método)

Recupera una secuencia de elementos del objeto Vector actual, empezando en el índice especificado, y los copia en la matriz asignada por el llamador.

### <a name="syntax"></a>Sintaxis

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>Parámetros

*startIndex*  
Índice basado en cero del principio de los elementos que se van a recuperar.

*dest*  
Una matriz asignada por el llamador de elementos que comienzan con el elemento especificado por *startIndex* y termina con el último elemento del vector.

### <a name="return-value"></a>Valor devuelto

Número de elementos recuperados.

### <a name="remarks"></a>Comentarios

Esta función no se ha diseñado para el uso en el código de cliente. Se usa internamente en el [to_vector (función)](../cppcx/to-vector-function.md) para habilitar la conversión eficaz de instancias Platform instancias std:: vector.

## <a name="getview"></a>Método vector:: GetView

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

*valor*  
El elemento que se va a buscar.

*index*  
Índice de base cero del elemento si parámetro *valor* se encuentra; en caso contrario, 0.

El *índice* parámetro es 0 si el elemento es el primer elemento del Vector o no se encontró el elemento. Si el valor devuelto es `true`, se encontró el elemento y es el primer elemento; de lo contrario, no se encuentra el elemento.

### <a name="return-value"></a>Valor devuelto

`true` si se encontró el elemento especificado; de lo contrario, `false`.

### <a name="remarks"></a>Comentarios

IndexOf utiliza std::find_if para buscar el elemento. Por tanto, los tipos de elementos personalizados deben sobrecargar los operadores == y != para habilitar las comparaciones de igualdad que requiere find_if.

##  <a name="insertat"></a>Vector:: InsertAt (método)

Inserta el elemento especificado en el objeto Vector actual detrás del elemento identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>Parámetros

*index*  
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

*item*  
Un elemento a insertar en el objeto Vector detrás del elemento especificado por *índice*. El tipo de *elemento* está definida por el *T* typename.

## <a name="removeat"></a>Vector:: RemoveAt (método)

Elimina el elemento identificado por el índice especificado del objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>Parámetros

*index*  
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

## <a name="removeatend"></a>Vector:: removeatend (método)

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

*arr*  
Una matriz de objetos cuyo tipo está definido por el *T* typename.

## <a name="setat"></a>Vector:: SetAt (método)

Asigna el valor especificado al elemento del objeto Vector actual identificado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>Parámetros

*index*  
Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.

*item*  
El valor que se va a asignar al elemento especificado. El tipo de *elemento* está definida por el *T* typename.

## <a name="size"></a>Vector:: Size (método)

Devuelve el número de elementos del objeto Vector actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del Vector actual.

## <a name="ctor"></a>Constructor vector:: vector

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

*a*  
A [std:: Array](../standard-library/array-class-stl.md) que se utilizará para inicializar el objeto Vector.

*arr*  
A [Platform:: Array](../cppcx/platform-array-class.md) que se utilizará para inicializar el objeto Vector.

*InIt*  
El tipo de una colección de objetos que se utiliza para inicializar el objeto Vector actual.

*il*  
A [std:: initializer_list](../standard-library/initializer-list-class.md) de objetos de tipo *T* que se utilizará para inicializar el objeto Vector.

*N*  
El número de elementos en una colección de objetos que se utiliza para inicializar el objeto Vector actual.

*size*  
El número de elementos del objeto Vector.

*valor*  
Un valor que se utiliza para inicializar cada elemento en el objeto Vector actual.

*v*  
Un [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a una [std:: vector](../standard-library/vector-class.md) que se usa para inicializar el objeto Vector actual.

*ptr*  
Puntero a un objeto `std::vector` que se usa para inicializar el objeto Vector actual.

*first*  
El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de *primer* se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*  
El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto Vector actual. El tipo de *última* se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Vea también

[Namespace de plataforma](platform-namespace-c-cx.md)  
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  