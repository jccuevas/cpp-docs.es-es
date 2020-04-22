---
title: Clase CAtlArray
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 607af2adaa3ef28a768812f3c811eb2ed3169ad9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748792"
---
# <a name="catlarray-class"></a>Clase CAtlArray

Esta clase implementa un objeto de matriz.

## <a name="syntax"></a>Sintaxis

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
Tipo de datos que se va a almacenar en la matriz.

*ETraits*<br/>
El código utilizado para copiar o mover elementos.

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Add (Agregar)](#add)|Llame a este método para agregar un elemento al objeto de matriz.|
|[Append](#append)|Llame a este método para agregar el contenido de una matriz al final de otra.|
|[Assertvalid](#assertvalid)|Llame a este método para confirmar que el objeto de matriz es válido.|
|[CAtlArray](#catlarray)|El constructor.|
|[•CAtlArray](#dtor)|Destructor.|
|[Copiar](#copy)|Llame a este método para copiar los elementos de una matriz a otra.|
|[FreeExtra](#freeextra)|Llame a este método para quitar los elementos vacíos de la matriz.|
|[GetAt](#getat)|Llame a este método para recuperar un solo elemento del objeto de matriz.|
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos almacenados en la matriz.|
|[GetData](#getdata)|Llame a este método para devolver un puntero al primer elemento de la matriz.|
|[InsertArrayAt](#insertarrayat)|Llame a este método para insertar una matriz en otra.|
|[InsertAt](#insertat)|Llame a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.|
|[IsEmpty](#isempty)|Llame a este método para probar si la matriz está vacía.|
|[Removeall](#removeall)|Llame a este método para quitar todos los elementos del objeto de matriz.|
|[RemoveAt](#removeat)|Llame a este método para quitar uno o varios elementos de la matriz.|
|[SetAt](#setat)|Llame a este método para establecer el valor de un elemento en el objeto de matriz.|
|[SetAtGrow](#setatgrow)|Llame a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.|
|[SetCount](#setcount)|Llame a este método para establecer el tamaño del objeto de matriz.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador &#91;&#93;](#operator_at)|Llame a este operador para devolver una referencia a un elemento de la matriz.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTIPO](#inargtype)|El tipo de datos que se va a utilizar para agregar elementos a la matriz.|
|[OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos de la matriz.|

## <a name="remarks"></a>Observaciones

`CAtlArray`proporciona métodos para crear y administrar una matriz de elementos de un tipo definido por el usuario. Aunque es similar a las `CAtlArray` matrices C estándar, el objeto puede reducirse dinámicamente y crecer según sea necesario. El índice de matriz siempre comienza en la posición 0, y el límite superior se puede fijar o permitir que se expanda a medida que se agregan nuevos elementos.

Para matrices con un pequeño número de elementos, se puede utilizar la clase ATL [CSimpleArray.](../../atl/reference/csimplearray-class.md)

`CAtlArray`está estrechamente relacionado con `CArray` la clase de MFC y funcionará en un proyecto MFC, aunque sin compatibilidad con la serialización.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray::Add

Llame a este método para agregar un elemento al objeto de matriz.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
El elemento que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del elemento agregado.

### <a name="remarks"></a>Observaciones

El nuevo elemento se agrega al final de la matriz. Si no se proporciona ningún elemento, se agrega un elemento vacío; es decir, la matriz aumenta de tamaño como si se hubiera agregado un elemento real. Si se produce un error en la operación, se llama a [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) con el argumento E_OUTOFMEMORY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::Append

Llame a este método para agregar el contenido de una matriz al final de otra.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parámetros

*aSrc*<br/>
Matriz que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Los elementos de la matriz proporcionada se agregan al final de la matriz existente. Si es necesario, se asignará memoria para dar cabida a los nuevos elementos.

Las matrices deben ser del mismo tipo y no es posible anexar una matriz a sí misma.

En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el argumento no es una matriz válida o si *aSrc* hace referencia al mismo objeto. En las compilaciones de versión, los argumentos no válidos pueden dar lugar a un comportamiento impredecible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Llame a este método para confirmar que el objeto de matriz es válido.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

Si el objeto de matriz no es válido, ATLASSERT producirá una aserción. Este método solo está disponible si se define _DEBUG.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

El constructor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el objeto de matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray::-CAtlArray

Destructor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos utilizados por el objeto de matriz.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray::Copy

Llame a este método para copiar los elementos de una matriz a otra.

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parámetros

*aSrc*<br/>
El origen de los elementos que se van a copiar en una matriz.

### <a name="remarks"></a>Observaciones

Llame a este método para sobrescribir los elementos de una matriz con los elementos de otra matriz. Si es necesario, se asignará memoria para dar cabida a los nuevos elementos. No es posible copiar elementos de una matriz a sí mismo.

Si se va a conservar el contenido existente de la matriz, utilice [CAtlArray::Append](#append) en su lugar.

En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el objeto existente no es válido o si *aSrc* hace referencia al mismo objeto. En las compilaciones de versión, los argumentos no válidos pueden dar lugar a un comportamiento impredecible.

> [!NOTE]
> `CAtlArray::Copy`no admite matrices que constan de elementos creados con la clase [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Llame a este método para quitar los elementos vacíos de la matriz.

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>Observaciones

Los elementos vacíos se quitan, pero el tamaño y el límite superior de la matriz permanecen sin cambios.

En compilaciones de depuración, se generará un ATLASSERT si el CAtlArray objeto no es válido, o si la matriz superaría su tamaño máximo.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt

Llame a este método para recuperar un único elemento del objeto de matriz.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El valor de índice del elemento de matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se generará un ATLASSERT si *iElement* supera el número de elementos de la matriz. En las compilaciones de versión, un argumento no válido puede dar lugar a un comportamiento impredecible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount

Llame a este método para devolver el número de elementos almacenados en la matriz.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos almacenados en la matriz.

### <a name="remarks"></a>Observaciones

Como el primer elemento de la matriz está `GetCount` en la posición 0, el valor devuelto por siempre es 1 mayor que el índice más grande.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray::GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData

Llame a este método para devolver un puntero al primer elemento de la matriz.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la ubicación de memoria que almacena el primer elemento de la matriz. Si no hay elementos disponibles, se devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

El tipo de datos que se va a utilizar para agregar elementos a la matriz.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Llame a este método para insertar una matriz en otra.

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parámetros

*iStart*<br/>
El índice en el que se va a insertar la matriz.

*paNew*<br/>
Matriz que se va a insertar.

### <a name="remarks"></a>Observaciones

Los elementos de la matriz *paNew* se copian en el objeto de matriz, comenzando en el elemento *iStart*. Los elementos de matriz existentes se mueven para evitar que se sobrescriban.

En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el objeto no es válido, o si el puntero *paNew* es NULL o no es válido.

> [!NOTE]
> `CAtlArray::InsertArrayAt`no admite matrices que constan de elementos creados con la clase [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt

Llame a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El índice donde se va a insertar el elemento o elementos.

*Elemento*<br/>
El valor del elemento o elementos que se van a insertar.

*nCount*<br/>
El número de elementos que se va a agregar.

### <a name="remarks"></a>Observaciones

Inserta uno o varios elementos en la matriz, empezando por *index iElement*. Los elementos existentes se mueven para evitar que se sobrescriban.

En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el objeto no es válido, el número de elementos que se van a agregar es cero o el número combinado de elementos es demasiado grande para que la matriz contenga. En las compilaciones comerciales, pasar parámetros no válidos puede provocar resultados impredecibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty

Llame a este método para probar si la matriz está vacía.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la matriz está vacía, false en caso contrario.

### <a name="remarks"></a>Observaciones

Se dice que la matriz está vacía si no contiene elementos. Por lo tanto, incluso si la matriz contiene elementos vacíos, no está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::operador []

Llame a este operador para devolver una referencia a un elemento de la matriz.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El valor de índice del elemento de matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

### <a name="remarks"></a>Observaciones

Realiza una función similar a [CAtlArray::GetAt](#getat). A diferencia de la clase MFC [CArray](../../mfc/reference/carray-class.md), este operador no se puede utilizar como sustituto de [CAtlArray::SetAt](#setat).

En compilaciones de depuración, se generará un ATLASSERT si *iElement* supera el número total de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede provocar resultados impredecibles.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos de la matriz.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::RemoveAll

Llame a este método para quitar todos los elementos del objeto de matriz.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Quita todos los elementos del objeto de matriz.

Este método llama a [CAtlArray::SetCount](#setcount) para cambiar el tamaño de la matriz y, posteriormente, libera cualquier memoria asignada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray::IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt

Llame a este método para quitar uno o varios elementos de la matriz.

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El índice del primer elemento que se va a quitar.

*nCount*<br/>
Número de elementos que se va a quitar.

### <a name="remarks"></a>Observaciones

Quita uno o más elementos de la matriz. Los elementos restantes se desplazan hacia abajo. El límite superior se reduce, pero la memoria no se libera hasta que se realiza una llamada a [CAtlArray::FreeExtra.](#freeextra)

En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el objeto no es válido, o si el total combinado de *iElement* y *nCount* supera el número total de elementos de la matriz. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados impredecibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Llame a este método para establecer el valor de un elemento en el objeto de matriz.

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El índice que apunta al elemento de matriz que se va a establecer.

*Elemento*<br/>
Nuevo valor del elemento especificado.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se generará un ATLASSERT si *iElement* supera el número de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede dar lugar a resultados impredecibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray::GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount

Llame a este método para establecer el tamaño del objeto de matriz.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parámetros

*nNewSize*<br/>
El tamaño requerido de la matriz.

*nGrowBy*<br/>
Valor utilizado para determinar el tamaño del búfer. Un valor de -1 hace que se utilice un valor calculado internamente.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la matriz se redimensiona correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

La matriz se puede aumentar o disminuir de tamaño. Si aumenta, se agregan elementos vacíos adicionales a la matriz. Si se reduce, los elementos con los índices más grandes se eliminarán y se liberará la memoria.

Utilice este método para establecer el tamaño de la matriz antes de usarla. Si `SetCount` no se utiliza, el proceso de adición de elementos —y la asignación de memoria posterior realizada— reducirá el rendimiento y la memoria de fragmentos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray::GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Llame a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El índice que apunta al elemento de matriz que se va a establecer.

*Elemento*<br/>
Nuevo valor del elemento especificado.

### <a name="remarks"></a>Observaciones

Reemplaza el valor del elemento al que apunta el índice. Si *iElement* es mayor que el tamaño actual de la matriz, la matriz aumenta automáticamente mediante una llamada a [CAtlArray::SetCount](#setcount). En compilaciones de depuración, se generará un `CAtlArray` ATLASSERT si el objeto no es válido. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados impredecibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Consulte también

[MMXSwarm Sample](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Muestra de marquesina](../../overview/visual-cpp-samples.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
