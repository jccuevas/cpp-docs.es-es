---
title: CAtlArray (clase)
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
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864896"
---
# <a name="catlarray-class"></a>CAtlArray (clase)

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
Código que se usa para copiar o quitar elementos.

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Add (Agregar)](#add)|Llame a este método para agregar un elemento al objeto de matriz.|
|[Append](#append)|Llame a este método para agregar el contenido de una matriz al final de otro.|
|[AssertValid](#assertvalid)|Llame a este método para confirmar que el objeto de matriz es válido.|
|[CAtlArray](#catlarray)|Constructor.|
|[~ CAtlArray](#dtor)|Destructor.|
|[Copy](#copy)|Llame a este método para copiar los elementos de una matriz en otra.|
|[FreeExtra](#freeextra)|Llame a este método para quitar todos los elementos vacíos de la matriz.|
|[GetAt](#getat)|Llame a este método para recuperar un único elemento del objeto de matriz.|
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos almacenados en la matriz.|
|[GetData](#getdata)|Llame a este método para devolver un puntero al primer elemento de la matriz.|
|[InsertArrayAt](#insertarrayat)|Llame a este método para insertar una matriz en otra.|
|[Insertat (](#insertat)|Llame a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.|
|[IsEmpty](#isempty)|Llame a este método para comprobar si la matriz está vacía.|
|[RemoveAll](#removeall)|Llame a este método para quitar todos los elementos del objeto de matriz.|
|[RemoveAt](#removeat)|Llame a este método para quitar uno o varios elementos de la matriz.|
|[SetAt](#setat)|Llame a este método para establecer el valor de un elemento en el objeto de matriz.|
|[SetAtGrow](#setatgrow)|Llame a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.|
|[SetCount](#setcount)|Llame a este método para establecer el tamaño del objeto de matriz.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[Operator&#91;&#93;](#operator_at)|Llame a este operador para devolver una referencia a un elemento de la matriz.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Tipo de datos que se va a utilizar para agregar elementos a la matriz.|
|[OUTARGTYPE](#outargtype)|Tipo de datos que se va a usar para recuperar los elementos de la matriz.|

## <a name="remarks"></a>Observaciones

`CAtlArray` proporciona métodos para crear y administrar una matriz de elementos de un tipo definido por el usuario. Aunque es similar a las matrices estándar de C, el objeto `CAtlArray` puede reducirse y crecer dinámicamente según sea necesario. El índice de la matriz siempre comienza en la posición 0 y el límite superior puede ser fijo o se puede expandir a medida que se agregan nuevos elementos.

En el caso de las matrices con un número pequeño de elementos, se puede usar la clase ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) .

`CAtlArray` está estrechamente relacionada con la clase `CArray` de MFC y funcionará en un proyecto MFC, aunque no admita la serialización.

Para obtener más información, vea [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll. h

##  <a name="add"></a>CAtlArray:: Add

Llame a este método para agregar un elemento al objeto de matriz.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parámetros

*Element*<br/>
Elemento que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del elemento agregado.

### <a name="remarks"></a>Observaciones

El nuevo elemento se agrega al final de la matriz. Si no se proporciona ningún elemento, se agrega un elemento vacío. es decir, la matriz aumenta de tamaño como si se hubiera agregado un elemento real. Si se produce un error en la operación, se llama a [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) con el argumento E_OUTOFMEMORY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>CAtlArray:: Append

Llame a este método para agregar el contenido de una matriz al final de otro.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parámetros

*aSrc*<br/>
Matriz que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Los elementos de la matriz proporcionada se agregan al final de la matriz existente. Si es necesario, se asignará memoria para alojar los nuevos elementos.

Las matrices deben ser del mismo tipo y no es posible anexar una matriz a sí misma.

En las compilaciones de depuración, se producirá una ATLASSERT si el argumento `CAtlArray` no es una matriz válida o si *aSrc* hace referencia al mismo objeto. En las compilaciones de versión, los argumentos no válidos pueden provocar un comportamiento impredecible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>CAtlArray:: AssertValid

Llame a este método para confirmar que el objeto de matriz es válido.

```
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

Si el objeto de matriz no es válido, ATLASSERT producirá una aserción. Este método solo está disponible si se define _DEBUG.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>CAtlArray:: CAtlArray

Constructor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el objeto de matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>CAtlArray:: ~ CAtlArray

Destructor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos utilizados por el objeto de matriz.

##  <a name="copy"></a>CAtlArray:: Copy

Llame a este método para copiar los elementos de una matriz en otra.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parámetros

*aSrc*<br/>
Origen de los elementos que se van a copiar en una matriz.

### <a name="remarks"></a>Observaciones

Llame a este método para sobrescribir los elementos de una matriz con los elementos de otra matriz. Si es necesario, se asignará memoria para alojar los nuevos elementos. No es posible copiar los elementos de una matriz en sí mismo.

Si el contenido existente de la matriz se va a conservar, use [CAtlArray:: Append](#append) en su lugar.

En las compilaciones de depuración, se generará una ATLASSERT si el objeto de `CAtlArray` existente no es válido o si *aSrc* hace referencia al mismo objeto. En las compilaciones de versión, los argumentos no válidos pueden provocar un comportamiento impredecible.

> [!NOTE]
> `CAtlArray::Copy` no admite matrices que consten de elementos creados con la clase [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>CAtlArray:: FreeExtra

Llame a este método para quitar todos los elementos vacíos de la matriz.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Observaciones

Se quitan los elementos vacíos, pero el tamaño y el límite superior de la matriz permanecen inalterados.

En las compilaciones de depuración, se generará una ATLASSERT si el objeto CAtlArray no es válido o si la matriz superaría su tamaño máximo.

##  <a name="getat"></a>CAtlArray:: GetAt

Llame a este método para recuperar un único elemento del objeto de matriz.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Valor de índice del elemento de la matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se generará un ATLASSERT si *IElement* supera el número de elementos de la matriz. En las compilaciones de versión, un argumento no válido puede provocar un comportamiento impredecible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>CAtlArray:: GetCount

Llame a este método para devolver el número de elementos almacenados en la matriz.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos almacenados en la matriz.

### <a name="remarks"></a>Observaciones

Como el primer elemento de la matriz está en la posición 0, el valor devuelto por `GetCount` es siempre 1 mayor que el índice más grande.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray:: GetAt](#getat).

##  <a name="getdata"></a>CAtlArray:: GetData

Llame a este método para devolver un puntero al primer elemento de la matriz.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la ubicación de memoria que almacena el primer elemento de la matriz. Si no hay elementos disponibles, se devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>CAtlArray:: INARGTYPE

Tipo de datos que se va a utilizar para agregar elementos a la matriz.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>CAtlArray:: InsertArrayAt

Llame a este método para insertar una matriz en otra.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parámetros

*iStart*<br/>
Índice en el que se va a insertar la matriz.

*paNew*<br/>
Matriz que se va a insertar.

### <a name="remarks"></a>Observaciones

Los elementos de la matriz *paNew* se copian en el objeto de matriz, comenzando en el elemento *iStart*. Los elementos de la matriz existentes se mueven para evitar que se sobrescriban.

En las compilaciones de depuración, se producirá una ATLASSERT si el objeto `CAtlArray` no es válido o si el puntero *paNew* es null o no es válido.

> [!NOTE]
> `CAtlArray::InsertArrayAt` no admite matrices que consten de elementos creados con la clase [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>CAtlArray:: Insertat (

Llame a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Índice en el que se van a insertar el elemento o los elementos.

*Element*<br/>
Valor del elemento o elementos que se van a insertar.

*nCount*<br/>
Número de elementos que se van a agregar.

### <a name="remarks"></a>Observaciones

Inserta uno o más elementos en la matriz, empezando por el índice *IElement*. Los elementos existentes se mueven para evitar que se sobrescriban.

En las compilaciones de depuración, se producirá una ATLASSERT si el objeto `CAtlArray` no es válido, si el número de elementos que se va a agregar es cero o si el número combinado de elementos es demasiado grande para que lo contenga la matriz. En las compilaciones comerciales, el paso de parámetros no válidos puede producir resultados imprevisibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>CAtlArray:: IsEmpty

Llame a este método para comprobar si la matriz está vacía.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la matriz está vacía; en caso contrario, false.

### <a name="remarks"></a>Observaciones

Se dice que la matriz está vacía si no contiene ningún elemento. Por lo tanto, incluso si la matriz contiene elementos vacíos, no está vacío.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>CAtlArray:: Operator []

Llame a este operador para devolver una referencia a un elemento de la matriz.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Valor de índice del elemento de la matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

### <a name="remarks"></a>Observaciones

Realiza una función similar a [CAtlArray:: GetAt](#getat). A diferencia de la clase MFC [CArray](../../mfc/reference/carray-class.md), este operador no se puede usar como sustituto de [CAtlArray:: SetAt](#setat).

En las compilaciones de depuración, se generará un ATLASSERT si *IElement* supera el número total de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede producir resultados imprevisibles.

##  <a name="outargtype"></a>CAtlArray:: OUTARGTYPE

Tipo de datos que se va a usar para recuperar los elementos de la matriz.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>CAtlArray:: RemoveAll

Llame a este método para quitar todos los elementos del objeto de matriz.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Quita todos los elementos del objeto de matriz.

Este método llama a [CAtlArray:: SetCount](#setcount) para cambiar el tamaño de la matriz y, posteriormente, libera cualquier memoria asignada.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray:: IsEmpty](#isempty).

##  <a name="removeat"></a>CAtlArray:: RemoveAt

Llame a este método para quitar uno o varios elementos de la matriz.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Índice del primer elemento que se va a quitar.

*nCount*<br/>
Número de elementos que se va a quitar.

### <a name="remarks"></a>Observaciones

Quita uno o más elementos de la matriz. Los elementos restantes se desplazan hacia abajo. El límite superior se reduce, pero no se libera memoria hasta que se realiza una llamada a [CAtlArray:: FreeExtra](#freeextra) .

En las compilaciones de depuración, se producirá una ATLASSERT si el objeto `CAtlArray` no es válido o si el total combinado de *IElement* y *nCount* supera el número total de elementos de la matriz. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados imprevisibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>CAtlArray:: SetAt

Llame a este método para establecer el valor de un elemento en el objeto de matriz.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Índice que apunta al elemento de la matriz que se va a establecer.

*Element*<br/>
Nuevo valor del elemento especificado.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se generará un ATLASSERT si *IElement* supera el número de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede producir resultados imprevisibles.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray:: GetAt](#getat).

##  <a name="setcount"></a>CAtlArray:: SetCount

Llame a este método para establecer el tamaño del objeto de matriz.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parámetros

*nNewSize*<br/>
Tamaño necesario de la matriz.

*nGrowBy*<br/>
Valor que se usa para determinar el tamaño del búfer. Un valor de-1 hace que se use un valor calculado internamente.

### <a name="return-value"></a>Valor devuelto

Devuelve true si se cambia el tamaño de la matriz correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

Se puede aumentar o reducir el tamaño de la matriz. Si se aumenta, se agregan elementos vacíos adicionales a la matriz. Si se reduce, se eliminarán los elementos con los índices más grandes y se liberará memoria.

Use este método para establecer el tamaño de la matriz antes de utilizarla. Si no se utiliza `SetCount`, el proceso de agregar elementos (y la asignación de memoria subsiguiente realizada) reducirá la memoria de fragmentos y el rendimiento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlArray:: GetData](#getdata).

##  <a name="setatgrow"></a>CAtlArray:: SetAtGrow

Llame a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Índice que apunta al elemento de la matriz que se va a establecer.

*Element*<br/>
Nuevo valor del elemento especificado.

### <a name="remarks"></a>Observaciones

Reemplaza el valor del elemento al que apunta el índice. Si *IElement* es mayor que el tamaño actual de la matriz, la matriz se aumenta automáticamente mediante una llamada a [CAtlArray:: SetCount](#setcount). En las compilaciones de depuración, se producirá una ATLASSERT si el objeto `CAtlArray` no es válido. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados imprevisibles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de marquesina](../../overview/visual-cpp-samples.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
