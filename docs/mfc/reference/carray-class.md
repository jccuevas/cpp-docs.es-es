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
ms.openlocfilehash: 3355e72c58365e97f8f3f8ce09754285f671915a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753982"
---
# <a name="carray-class"></a>CArray (clase)

Admite matrices que son como matrices C, pero pueden reducir se y crecer dinámicamente según sea necesario.

## <a name="syntax"></a>Sintaxis

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro Template que especifica el tipo de objetos almacenados en la matriz. *TYPE* es un parámetro `CArray`devuelto por .

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumento que se utiliza para tener acceso a los objetos almacenados en la matriz. A menudo una referencia a *TIPO*. *ARG_TYPE* es un parámetro `CArray`que se pasa a .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArray::CArray](#carray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArray::Add](#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CArray::Append](#append)|Anexa otra matriz a la matriz; crece la matriz si es necesario|
|[CArray::Copiar](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CArray::ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CArray::FreeExtra](#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CArray::GetAt](#getat)|Devuelve el valor en un índice dado.|
|[CArray::GetCount](#getcount)|Obtiene el número de elementos de esta matriz.|
|[CArray::GetData](#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CArray::GetSize](#getsize)|Obtiene el número de elementos de esta matriz.|
|[CArray::GetUpperBound](#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CArray::InsertAt](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CArray::IsEmpty](#isempty)|Determina si la matriz está vacía.|
|[CArray::RemoveAll](#removeall)|Quita todos los elementos de esta matriz.|
|[CArray::RemoveAt](#removeat)|Quita un elemento en un índice específico.|
|[CArray::SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CArray::SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CArray::SetSize](#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

Los índices de matriz siempre comienzan en la posición 0. Puede decidir si desea corregir el límite superior o habilitar la matriz para expandirse al agregar elementos más allá del límite actual. La memoria se asigna de forma contigua al límite superior, incluso si algunos elementos son null.

> [!NOTE]
> La mayoría de `CArray` los métodos que cambian el tamaño de un objeto o le agregan elementos utilizan [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) para mover elementos. Esto es un `memcpy_s` problema porque no es compatible con los objetos que requieren que se llame al constructor. Si los elementos del `CArray` `memcpy_s`archivo no son `CArray` compatibles con , debe crear un nuevo tamaño adecuado. A continuación, debe utilizar [CArray::Copy](#copy) y [CArray::SetAt](#setat) para rellenar la `memcpy_s`nueva matriz porque esos métodos utilizan un operador de asignación en lugar de .

Al igual que con una matriz `CArray` C, el tiempo de acceso para un elemento indizado es constante y es independiente del tamaño de la matriz.

> [!TIP]
> Antes de usar una matriz, utilice [SetSize](#setsize) para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Si necesita un volcado de elementos individuales en una matriz, debe establecer la profundidad de la [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto a 1 o mayor.

Ciertas funciones miembro de esta clase llaman a funciones auxiliares globales que se deben personalizar para la mayoría de los usos de la `CArray` clase. Vea el tema [Ayudantes de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección Macros y globales de MFC.

La derivación de la clase de matriz es como la derivación de la lista.

Para obtener más información `CArray`acerca de cómo usar , vea el artículo [Colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::Add

Agrega un nuevo elemento al final de una matriz, aumentando la matriz en 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumentos que hacen referencia a elementos en esta matriz.

*newElement*<br/>
El elemento que se va a agregar a esta matriz.

### <a name="return-value"></a>Valor devuelto

El índice del elemento agregado.

### <a name="remarks"></a>Observaciones

Si [SetSize](#setsize) se ha `nGrowBy` utilizado con un valor mayor que 1, se puede asignar memoria adicional. Sin embargo, el límite superior aumentará en sólo 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::Append

Llame a esta función miembro para agregar el contenido de una matriz al final de otra.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a anexar a una matriz.

### <a name="return-value"></a>Valor devuelto

El índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Las matrices deben ser del mismo tipo.

Si es `Append` necesario, puede asignar memoria adicional para dar cabida a los elementos anexados a la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray::CArray

Construye una matriz vacía.

```
CArray();
```

### <a name="remarks"></a>Observaciones

La matriz crece un elemento a la vez.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::Copiar

Utilice esta función miembro para copiar los elementos de una matriz a otra.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a copiar en una matriz.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para sobrescribir los elementos de una matriz con los elementos de otra matriz.

`Copy`no libera memoria; sin embargo, `Copy` si es necesario, puede asignar memoria adicional para acomodar los elementos copiados en la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray::ElementAt

Devuelve una referencia temporal al elemento especificado dentro de la matriz.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valor devuelto

Una referencia a un elemento de matriz.

### <a name="remarks"></a>Observaciones

Se utiliza para implementar el operador de asignación del lado izquierdo para matrices.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetSize](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra

Libera cualquier memoria adicional que se haya asignado mientras se cultivaba la matriz.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Observaciones

Esta función no tiene ningún efecto sobre el tamaño o el límite superior de la matriz.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetData](#getdata).

## <a name="carraygetat"></a><a name="getat"></a>CArray::GetAt

Devuelve el elemento de matriz en el índice especificado.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de matriz.

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Valor devuelto

El elemento de matriz actualmente en este índice.

### <a name="remarks"></a>Observaciones

Si se pasa un valor negativo o `GetUpperBound` un valor mayor que el valor devuelto por, se producirá un error en la aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray::GetCount

Devuelve el número de elementos de matriz.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos de la matriz. Dado que los índices se basan en cero, el tamaño es 1 mayor que el índice más grande. Llamar a este método generará el mismo resultado que el [CArray::GetSize](#getsize) método.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray::GetData

Utilice esta función miembro para obtener acceso directo a los elementos de una matriz.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de matriz.

### <a name="return-value"></a>Valor devuelto

Puntero a un elemento de matriz.

### <a name="remarks"></a>Observaciones

Si no hay `GetData` elementos disponibles, devuelve un valor nulo.

Aunque el acceso directo a los elementos de una matriz `GetData`puede ayudarle a trabajar más rápidamente, tenga cuidado al llamar; los errores que comete afectan directamente a los elementos de la matriz.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray::GetSize

Devuelve el tamaño de la matriz.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Observaciones

Dado que los índices se basan en cero, el tamaño es 1 mayor que el índice más grande. Llamar a este método generará el mismo resultado que el [CArray::GetCount](#getcount) método.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound

Devuelve el límite superior actual de esta matriz.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Observaciones

Dado que los índices de matriz se basan `GetSize`en cero, esta función devuelve un valor 1 menor que .

La `GetUpperBound( )` condición -1 indica que la matriz no contiene elementos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArray::GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray::InsertAt

La primera `InsertAt` versión de inserta un elemento (o varias copias de un elemento) en un índice especificado en una matriz.

```cpp
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
Un índice entero que puede ser `GetUpperBound`mayor que el valor devuelto por .

*ARG_TYPE*<br/>
Parámetro template que especifica el tipo de elementos de esta matriz.

*newElement*<br/>
El elemento que se va a colocar en esta matriz.

*nCount*<br/>
El número de veces que se debe insertar este elemento (valor predeterminado es 1).

*nStartIndex*<br/>
Un índice entero que puede ser mayor que el valor devuelto por [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Otra matriz que contiene elementos que se agregarán a esta matriz.

### <a name="remarks"></a>Observaciones

En el proceso, desplaza hacia arriba (incrementando el índice) el elemento existente en este índice y desplaza hacia arriba todos los elementos por encima de él.

La segunda versión inserta todos `CArray` los elementos de otra colección, comenzando en la posición *nStartIndex.*

La `SetAt` función, en cambio, reemplaza un elemento de matriz especificado y no desplaza ningún elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray::IsEmpty

Determina si la matriz está vacía.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la matriz no contiene elementos; de lo contrario 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::operador\[\]

Estos operadores de subíndice son un sustituto conveniente para el [SetAt](#setat) y [GetAt](#getat) funciones.

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro template que especifica el tipo de elementos de esta matriz.

*nIndex*<br/>
Indice del elemento al que se va a tener acceso.

### <a name="remarks"></a>Observaciones

El primer operador, llamado para matrices que no son **const**, se puede utilizar en la derecha (valor r) o a la izquierda (valor l) de una instrucción de asignación. El segundo, llamado para **matrices const,** sólo se puede utilizar a la derecha.

La versión de depuración de la biblioteca afirma si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de los límites.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::RelocateElements

Reubica los datos en un nuevo búfer cuando la matriz debe crecer o reducirse.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*pNewData*<br/>
Un nuevo búfer para la matriz de elementos.

*pData*<br/>
La antigua matriz de elementos.

*nCount*<br/>
Número de elementos de la matriz antigua.

### <a name="remarks"></a>Observaciones

*pNewData* siempre es lo suficientemente grande como para contener todos los elementos *pData.*

La implementación de [CArray](../../mfc/reference/carray-class.md) utiliza este método para copiar los datos antiguos en un nuevo búfer cuando la matriz debe crecer o reducirse (cuando se llama a [SetSize](#setsize) o [FreeExtra).](#freeextra) La implementación predeterminada solo copia los datos.

Para las matrices en las que un elemento contiene un puntero a uno de sus propios miembros, u otra estructura contiene un puntero a uno de los elementos de matriz, los punteros no se actualizan en copia sin formato. En este caso, puede corregir punteros `RelocateElements` implementando una especialización de con los tipos relevantes. También es responsable de la copia de datos.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray::RemoveAll

Quita todos los elementos de esta matriz.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Si la matriz ya está vacía, la función sigue funcionando.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray::RemoveAt

Quita uno o varios elementos a partir de un índice especificado en una matriz.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

*nCount*<br/>
Número de elementos que se va a quitar.

### <a name="remarks"></a>Observaciones

En el proceso, desplaza hacia abajo todos los elementos por encima de los elementos eliminados. Disminuye el límite superior de la matriz, pero no libera memoria.

Si intenta quitar más elementos de los que se encuentran en la matriz por encima del punto de eliminación, la versión de depuración de la biblioteca afirma.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray::SetAt

Establece el elemento de matriz en el índice especificado.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de argumentos utilizados para hacer referencia a elementos de matriz.

*newElement*<br/>
El nuevo valor de elemento que se almacenará en la posición especificada.

### <a name="remarks"></a>Observaciones

`SetAt`no hará que la matriz crezca. Utilice [SetAtGrow](#setatgrow) si desea que la matriz crezca automáticamente.

Debe asegurarse de que el valor de índice representa una posición válida en la matriz. Si está fuera de los límites, la versión de depuración de la biblioteca afirma.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray::SetAtGrow

Establece el elemento de matriz en el índice especificado.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la matriz.

*newElement*<br/>
El elemento que se va a agregar a esta matriz. Se permite un valor NULL.

### <a name="remarks"></a>Observaciones

La matriz crece automáticamente si es necesario (es decir, el límite superior se ajusta para dar cabida al nuevo elemento).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::SetSize

Establece el tamaño de una matriz vacía o existente; asigna memoria si es necesario.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parámetros

*nNewSize*<br/>
El nuevo tamaño de matriz (número de elementos). Debe ser mayor o igual que 0.

*nGrowBy*<br/>
El número mínimo de ranuras de elementos que se asignarán si es necesario un aumento de tamaño.

### <a name="remarks"></a>Observaciones

Si el nuevo tamaño es menor que el tamaño anterior, la matriz se trunca y se libera toda la memoria no utilizada.

Utilice esta función para establecer el tamaño de la matriz antes de empezar a utilizar la matriz. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

El parámetro *nGrowBy* afecta a la asignación de memoria interna mientras la matriz está creciendo. Su uso nunca afecta al tamaño de la matriz según lo informado por [GetSize](#getsize) y [GetUpperBound](#getupperbound). Si se utiliza el valor predeterminado, MFC asigna memoria de una manera calculada para evitar la fragmentación de la memoria y optimizar la eficiencia para la mayoría de los casos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetData](#getdata).

## <a name="see-also"></a>Vea también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CObArray](../../mfc/reference/cobarray-class.md)<br/>
[Asistentes de clase de colección](../../mfc/reference/collection-class-helpers.md)
