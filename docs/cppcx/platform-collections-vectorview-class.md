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
ms.openlocfilehash: 02b5e15a816ec057bfb0a8201b7591e628c3ea2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161386"
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

### <a name="remarks"></a>Comentarios

El `VectorView` la clase implementa la [Windows::Foundation::Collections::IVectorView\<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_) interfaz y la compatibilidad con los iteradores de la biblioteca de plantillas estándar.

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|Inicializa una nueva instancia de la clase VectorView.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[VectorView::First](#first)|Devuelve un iterador que especifica el primer elemento del objeto VectorView.|
|[VectorView::GetAt](#getat)|Recupera el elemento del objeto VectorView actual indicado por el índice especificado.|
|[VectorView::GetMany](#getmany)|Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.|
|[VectorView::IndexOf](#indexof)|Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.|
|[VectorView::Size](#size)|Devuelve el número de elementos del objeto VectorView actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VectorView`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Platform::Collections

## <a name="first"></a>  Vectorview (método)

Devuelve un iterador que especifica el primer elemento del objeto VectorView.

### <a name="syntax"></a>Sintaxis

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del objeto VectorView.

### <a name="remarks"></a>Comentarios

Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myVectorView->First();`.

## <a name="getat"></a>  Vectorview (método)

Recupera el elemento del objeto VectorView actual indicado por el índice especificado.

### <a name="syntax"></a>Sintaxis

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Entero sin signo de base cero que especifica un elemento determinado en el objeto VectorView.

### <a name="return-value"></a>Valor devuelto

Elemento especificado por el parámetro `index`. El tipo de elemento especificado por el parámetro de plantilla VectorView *T*.

## <a name="getmany"></a>  Getmany (método)

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

## <a name="indexof"></a>  Vectorview (método)

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

*index*<br/>
El índice de base cero del elemento si se encuentra el parámetro `value`; en caso contrario, 0.

El *índice* parámetro es 0 si el elemento o es el primer elemento de la `VectorView` o no se encontró el elemento. Si el valor devuelto es **true**, se encontró el elemento y es el primer elemento; en caso contrario, no se encontró el elemento.

### <a name="return-value"></a>Valor devuelto

**True** si el elemento especificado se encuentra; en caso contrario, **false**.

## <a name="size"></a>  Vectorview (método)

Devuelve el número de elementos del objeto VectorView actual.

### <a name="syntax"></a>Sintaxis

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto VectorView actual.

## <a name="ctor"></a>  Constructor Vectorview

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

*InIt*<br/>
El tipo de una colección de objetos que se utiliza para inicializar el objeto VectorView actual.

*il*<br/>
Un [std:: initializer_list](../standard-library/initializer-list-class.md) cuyos elementos se usará para inicializar el objeto VectorView.

*N*<br/>
El número de elementos en una colección de objetos que se utiliza para inicializar el objeto VectorView actual.

*size*<br/>
El número de elementos del objeto VectorView.

*value*<br/>
Un valor que se utiliza para inicializar cada elemento en el objeto VectorView actual.

*v*<br/>
Un [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [std:: vector](../standard-library/vector-class.md) que se usa para inicializar el objeto VectorView actual.

*ptr*<br/>
Puntero a un objeto `std::vector` que se usa para inicializar el objeto VectorView actual.

*arr*<br/>
Un [Platform:: Array](../cppcx/platform-array-class.md) objeto que se usa para inicializar el objeto VectorView actual.

*a*<br/>
Un [std:: Array](../standard-library/array-class-stl.md) objeto que se usa para inicializar el objeto VectorView actual.

*first*<br/>
El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `first` se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

*last*<br/>
El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `last` se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
