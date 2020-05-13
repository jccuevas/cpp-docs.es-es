---
title: Platform::Collections::VectorView (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: 7f12c7b926cd8d3d8fc892cff6f2245e7c216219
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032231"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView (Clase)

Representa una vista de solo lectura de una colección secuencial de objetos a los que se puede obtener acceso individualmente por índice. El parámetro de plantilla especifica el tipo de cada objeto de la colección.

## <a name="syntax"></a>Sintaxis

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de los elementos contenidos en el objeto `VectorView` .

*E*<br/>
Especifica un predicado binario para probar la igualdad con valores de tipo `T`. El valor predeterminado es `std::equal_to<T>`.

### <a name="remarks"></a>Observaciones

La `VectorView` clase implementa la interfaz [de>Windows::Foundation::Collections::IVectorView\<T](/uwp/api/windows.foundation.collections.ivectorview-1) y admite los iteradores de la biblioteca de plantillas estándar.

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|Inicializa una nueva instancia de la clase VectorView.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[VectorView::Primero](#first)|Devuelve un iterador que especifica el primer elemento del objeto VectorView.|
|[VectorView::GetAt](#getat)|Recupera el elemento del objeto VectorView actual indicado por el índice especificado.|
|[VectorView::GetMany](#getmany)|Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.|
|[VectorView::IndexOf](#indexof)|Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.|
|[VectorView::Size](#size)|Devuelve el número de elementos del objeto VectorView actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VectorView`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView::Primer método

Devuelve un iterador que especifica el primer elemento del objeto VectorView.

### <a name="syntax"></a>Sintaxis

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del objeto VectorView.

### <a name="remarks"></a>Observaciones

Una forma cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo: `auto x = myVectorView->First();`.

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView::GetAt Método

Recupera el elemento del objeto VectorView actual indicado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parámetros

*índice*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto VectorView.

### <a name="return-value"></a>Valor devuelto

Elemento especificado por el parámetro `index`. El tipo de elemento se especifica mediante el parámetro de plantilla VectorView, *T*.

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView::GetMany Método

Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.

### <a name="syntax"></a>Sintaxis

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>Parámetros

*startIndex*<br/>
Índice basado en cero del principio de los elementos que se van a recuperar.

*dest*<br/>
Cuando se completa esta operación, matriz de elementos que empieza con el elemento especificado por `startIndex` y termina con el último elemento del objeto VectorView.

### <a name="return-value"></a>Valor devuelto

Número de elementos recuperados.

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView::IndexOf Método

Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.

### <a name="syntax"></a>Sintaxis

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
El elemento que se va a buscar.

*índice*<br/>
El índice de base cero del elemento si se encuentra el parámetro `value`; en caso contrario, 0.

El parámetro *index* es 0 si el elemento `VectorView` es el primer elemento del elemento o no se encontró. Si el valor devuelto es **true**, se encontró el elemento y es el primer elemento; de lo contrario, el artículo no se encontró.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra el elemento especificado; de lo contrario, **false**.

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView::Método size

Devuelve el número de elementos del objeto VectorView actual.

### <a name="syntax"></a>Sintaxis

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto VectorView actual.

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView::VectorView Constructor

Inicializa una nueva instancia de la clase VectorView.

### <a name="syntax"></a>Sintaxis

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>Parámetros

*Init*<br/>
El tipo de una colección de objetos que se utiliza para inicializar el objeto VectorView actual.

*Il*<br/>
Un [std::initializer_list](../standard-library/initializer-list-class.md) cuyos elementos se utilizarán para inicializar el VectorView.

*N*<br/>
El número de elementos en una colección de objetos que se utiliza para inicializar el objeto VectorView actual.

*size*<br/>
El número de elementos del objeto VectorView.

*value*<br/>
Un valor que se utiliza para inicializar cada elemento en el objeto VectorView actual.

*Ⅴ*<br/>
Un [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [std::vector](../standard-library/vector-class.md) que se utiliza para inicializar el VectorView actual.

*Ptr*<br/>
Puntero a un objeto `std::vector` que se usa para inicializar el objeto VectorView actual.

*Arr*<br/>
Un [Platform::Array](../cppcx/platform-array-class.md) objeto que se utiliza para inicializar el VectorView actual.

*Un*<br/>
Un [std::array](../standard-library/array-class-stl.md) objeto que se utiliza para inicializar el VectorView actual.

*first*<br/>
El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo `first` de se pasa por medio de *reenvío perfecto.* Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo `last` de se pasa por medio de *reenvío perfecto.* Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
