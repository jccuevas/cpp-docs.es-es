---
title: CArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: f82dbf7dce2e14bf760bb76d23d23f667797ee0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424600"
---
# <a name="carray-class"></a>CArray (clase)

Admite matrices que son como matrices de C, pero puede reducir y crecer dinámicamente según sea necesario.

## <a name="syntax"></a>Sintaxis

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Parámetro de plantilla que especifica el tipo de objetos almacenados en la matriz. El *tipo* es un parámetro devuelto por `CArray`.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumento que se utiliza para tener acceso a los objetos almacenados en la matriz. A menudo, es una referencia al *tipo*. *ARG_TYPE* es un parámetro que se pasa a `CArray`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArray:: CArray](#carray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArray:: Add](#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CArray:: Append](#append)|Anexa otra matriz a la matriz; aumenta la matriz si es necesario.|
|[CArray:: Copy](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CArray:: ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CArray:: FreeExtra](#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CArray:: GetAt](#getat)|Devuelve el valor en un índice dado.|
|[CArray:: GetCount](#getcount)|Obtiene el número de elementos de esta matriz.|
|[CArray:: GetData](#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CArray:: obtiene](#getsize)|Obtiene el número de elementos de esta matriz.|
|[CArray:: GetUpperBound](#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CArray:: Insertat (](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CArray:: IsEmpty](#isempty)|Determina si la matriz está vacía.|
|[CArray:: RemoveAll](#removeall)|Quita todos los elementos de esta matriz.|
|[CArray:: RemoveAt](#removeat)|Quita un elemento en un índice específico.|
|[CArray:: SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CArray:: SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CArray:: setSize](#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

Los índices de matriz siempre se inician en la posición 0. Puede decidir si desea corregir el límite superior o habilitar la expansión de la matriz al agregar elementos más allá del límite actual. La memoria se asigna de forma contigua al límite superior, aunque algunos elementos sean null.

> [!NOTE]
>  La mayoría de los métodos que cambia el tamaño de un objeto `CArray` o agrega elementos al mismo usan [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) para Desplace los elementos. Se trata de un problema porque `memcpy_s` no es compatible con ningún objeto que requiera la llamada al constructor. Si los elementos de la `CArray` no son compatibles con `memcpy_s`, debe crear un nuevo `CArray` del tamaño adecuado. Después, debe usar [CArray:: Copy](#copy) y [CArray:: SetAt](#setat) para rellenar la nueva matriz, ya que esos métodos usan un operador de asignación en lugar de `memcpy_s`.

Al igual que con una matriz de C, el tiempo de acceso de un elemento indizado `CArray` es constante y es independiente del tamaño de la matriz.

> [!TIP]
>  Antes de usar una matriz, use [setSize](#setsize) para establecer su tamaño y asignar memoria para ella. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Si necesita un volcado de elementos individuales en una matriz, debe establecer la profundidad del objeto [CDumpContext](../../mfc/reference/cdumpcontext-class.md) en 1 o más.

Ciertas funciones miembro de esta clase llaman a funciones auxiliares globales que se deben personalizar para la mayoría de los usos de la clase `CArray`. Vea el tema [aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección macros y variables globales de MFC.

La derivación de la clase de matriz es como derivación de lista.

Para obtener más información sobre cómo usar `CArray`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

##  <a name="add"></a>CArray:: Add

Agrega un nuevo elemento al final de una matriz, aumentando la matriz en 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumentos que hacen referencia a los elementos de esta matriz.

*newElement*<br/>
Elemento que se va a agregar a esta matriz.

### <a name="return-value"></a>Valor devuelto

Índice del elemento agregado.

### <a name="remarks"></a>Observaciones

Si se ha usado [setSize](#setsize) con un valor `nGrowBy` mayor que 1, se puede asignar memoria adicional. Sin embargo, el límite superior aumentará en 1 solo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>CArray:: Append

Llame a esta función miembro para agregar el contenido de una matriz al final de otro.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a anexar a una matriz.

### <a name="return-value"></a>Valor devuelto

Índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Las matrices deben ser del mismo tipo.

Si es necesario, `Append` puede asignar memoria adicional para dar cabida a los elementos anexados a la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>CArray:: CArray

Construye una matriz vacía.

```
CArray();
```

### <a name="remarks"></a>Observaciones

La matriz crece un elemento cada vez.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>CArray:: Copy

Utilice esta función miembro para copiar los elementos de una matriz en otra.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a copiar en una matriz.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para sobrescribir los elementos de una matriz con los elementos de otra matriz.

`Copy` no libera memoria; sin embargo, si es necesario, `Copy` puede asignar memoria adicional para dar cabida a los elementos copiados en la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>CArray:: ElementAt

Devuelve una referencia temporal al elemento especificado de la matriz.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valor devuelto

Referencia a un elemento de la matriz.

### <a name="remarks"></a>Observaciones

Se utiliza para implementar el operador de asignación del lado izquierdo para las matrices.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de se [obtiene](#getsize).

##  <a name="freeextra"></a>CArray:: FreeExtra

Libera cualquier memoria adicional que se asignó mientras se aumentó la matriz.

```
void FreeExtra();
```

### <a name="remarks"></a>Observaciones

Esta función no tiene ningún efecto en el tamaño o el límite superior de la matriz.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetData](#getdata).

##  <a name="getat"></a>CArray:: GetAt

Devuelve el elemento de matriz que se encuentra en el índice especificado.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la matriz.

*nIndex*<br/>
Índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valor devuelto

Elemento de la matriz que se encuentra actualmente en este índice.

### <a name="remarks"></a>Observaciones

Si se pasa un valor negativo o un valor mayor que el valor devuelto por `GetUpperBound`, se producirá un error en una aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>CArray:: GetCount

Devuelve el número de elementos de la matriz.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos de la matriz. Dado que los índices son de base cero, el tamaño es 1 mayor que el índice más grande. Si se llama a este método, se genera el mismo resultado que el método [CArray:: se obtiene](#getsize) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>CArray:: GetData

Utilice esta función miembro para obtener acceso directo a los elementos de una matriz.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la matriz.

### <a name="return-value"></a>Valor devuelto

Un puntero a un elemento de la matriz.

### <a name="remarks"></a>Observaciones

Si no hay elementos disponibles, `GetData` devuelve un valor null.

Aunque el acceso directo a los elementos de una matriz puede ayudarle a trabajar más rápidamente, tenga cuidado al llamar a `GetData`; cualquier error que haga directamente afectará a los elementos de la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>CArray:: obtiene

Devuelve el tamaño de la matriz.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Observaciones

Dado que los índices son de base cero, el tamaño es 1 mayor que el índice más grande. Si se llama a este método, se genera el mismo resultado que el método [CArray:: GetCount](#getcount) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>CArray:: GetUpperBound

Devuelve el límite superior actual de esta matriz.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Observaciones

Dado que los índices de matriz son de base cero, esta función devuelve un valor 1 menor que `GetSize`.

La condición `GetUpperBound( )` =-1 indica que la matriz no contiene ningún elemento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArray:: GetAt](#getat).

##  <a name="insertat"></a>CArray:: Insertat (

La primera versión de `InsertAt` inserta un elemento (o varias copias de un elemento) en un índice especificado de una matriz.

```
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice entero que puede ser mayor que el valor devuelto por `GetUpperBound`.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elementos de esta matriz.

*newElement*<br/>
Elemento que se va a colocar en esta matriz.

*nCount*<br/>
Número de veces que se debe insertar este elemento (el valor predeterminado es 1).

*nStartIndex*<br/>
Índice entero que puede ser mayor que el valor devuelto por [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Otra matriz que contiene los elementos que se van a agregar a esta matriz.

### <a name="remarks"></a>Observaciones

En el proceso, se desplaza hacia arriba (incrementando el índice) el elemento existente en este índice y desplaza todos los elementos situados por encima de él.

La segunda versión inserta todos los elementos de otra `CArray` colección, comenzando en la posición *nStartIndex* .

En cambio, la función `SetAt` reemplaza a un elemento especificado de la matriz y no desplaza los elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>CArray:: IsEmpty

Determina si la matriz está vacía.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la matriz no contiene elementos; de lo contrario, es 0.

##  <a name="operator_at"></a>CArray:: Operator \[\]

Estos operadores de subíndice son un sustituto adecuado para las funciones [SetAt](#setat) y [GetAt](#getat) .

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elementos de esta matriz.

*nIndex*<br/>
Índice del elemento al que se va a obtener acceso.

### <a name="remarks"></a>Observaciones

El primer operador, al que se llama para las matrices que no son **const**, se puede usar tanto en la derecha (r-value) como en la izquierda (valor l) de una instrucción de asignación. La segunda, llamada para matrices **const** , solo se puede usar a la derecha.

La versión de depuración de la biblioteca valida si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de los límites.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>CArray:: RelocateElements

Reubica los datos en un nuevo búfer cuando la matriz debe aumentar o disminuir.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*pNewData*<br/>
Nuevo búfer para la matriz de elementos.

*pData*<br/>
Matriz de elementos antigua.

*nCount*<br/>
Número de elementos de la matriz anterior.

### <a name="remarks"></a>Observaciones

*pNewData* siempre es lo suficientemente grande como para contener todos los elementos *pdata* .

La implementación de [CArray](../../mfc/reference/carray-class.md) usa este método para copiar los datos antiguos en un nuevo búfer cuando la matriz debe aumentar o reducirse (cuando se llama a [setSize](#setsize) o [FreeExtra](#freeextra) ). La implementación predeterminada simplemente copia los datos.

En el caso de las matrices en las que un elemento contiene un puntero a uno de sus miembros, u otra estructura que contiene un puntero a uno de los elementos de la matriz, los punteros no se actualizan en una copia simple. En este caso, puede corregir los punteros implementando una especialización de `RelocateElements` con los tipos pertinentes. También es responsable de la copia de datos.

##  <a name="removeall"></a>CArray:: RemoveAll

Quita todos los elementos de esta matriz.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Si la matriz ya está vacía, la función sigue funcionando.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>CArray:: RemoveAt

Quita uno o varios elementos a partir de un índice especificado de una matriz.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

*nCount*<br/>
Número de elementos que se va a quitar.

### <a name="remarks"></a>Observaciones

En el proceso, desplaza todos los elementos por encima de los elementos quitados. Disminuye el límite superior de la matriz pero no libera memoria.

Si intenta quitar más elementos de los contenidos en la matriz sobre el punto de eliminación, la versión de depuración de la biblioteca lo valida.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>CArray:: SetAt

Establece el elemento de matriz en el índice especificado.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumentos usado para hacer referencia a los elementos de la matriz.

*newElement*<br/>
Nuevo valor del elemento que se va a almacenar en la posición especificada.

### <a name="remarks"></a>Observaciones

`SetAt` no hará que la matriz crezca. Use [SetAtGrow](#setatgrow) si desea que la matriz crezca automáticamente.

Debe asegurarse de que el valor de índice representa una posición válida en la matriz. Si está fuera de los límites, se valida la versión de depuración de la biblioteca.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetAt](#getat).

##  <a name="setatgrow"></a>CArray:: SetAtGrow

Establece el elemento de matriz en el índice especificado.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice entero que es mayor o igual que 0.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la matriz.

*newElement*<br/>
Elemento que se va a agregar a esta matriz. Se permite un valor NULL.

### <a name="remarks"></a>Observaciones

La matriz crece automáticamente si es necesario (es decir, el límite superior se ajusta para acomodar el nuevo elemento).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>CArray:: setSize

Establece el tamaño de una matriz vacía o existente; asigna memoria si es necesario.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parámetros

*nNewSize*<br/>
Nuevo tamaño de la matriz (número de elementos). Debe ser mayor o igual a 0.

*nGrowBy*<br/>
Número mínimo de espacios de elementos que se van a asignar si es necesario un aumento de tamaño.

### <a name="remarks"></a>Observaciones

Si el nuevo tamaño es menor que el tamaño anterior, la matriz se trunca y se libera toda la memoria no utilizada.

Utilice esta función para establecer el tamaño de la matriz antes de empezar a usar la matriz. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

El parámetro *nGrowBy* afecta a la asignación de memoria interna mientras la matriz crece. Su uso nunca afecta al tamaño de la matriz tal y como se muestra en [GetUpperBound](#getupperbound) [y en](#getsize) . Si se usa el valor predeterminado, MFC asigna memoria de una forma calculada para evitar la fragmentación de la memoria y optimizar la eficacia en la mayoría de los casos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetData](#getdata).

## <a name="see-also"></a>Consulte también

[Ejemplo de recopilación de MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObArray (clase)](../../mfc/reference/cobarray-class.md)<br/>
[Asistentes de clase de colección](../../mfc/reference/collection-class-helpers.md)
