---
title: Clase CTypedPtrArray
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: a996bca471ce82a7c2adaaad67670ddef417eda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373279"
---
# <a name="ctypedptrarray-class"></a>Clase CTypedPtrArray

Proporciona un "contenedor" con seguridad de tipos para objetos de clase `CPtrArray` o `CObArray`.

## <a name="syntax"></a>Sintaxis

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Clase base de la clase de matriz de puntero con tipo; debe ser una `CObArray` clase `CPtrArray`de matriz ( o ).

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|Agrega un nuevo elemento al final de una matriz. Crece la matriz si es necesario|
|[CTypedPtrArray::Append](#append)|Agrega el contenido de una matriz al final de otra. Crece la matriz si es necesario|
|[CTypedPtrArray::Copy](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CTypedPtrArray::ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CTypedPtrArray::GetAt](#getat)|Devuelve el valor en un índice dado.|
|[CTypedPtrArray::InsertAt](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CTypedPtrArray::SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTypedPtrArray::operator \[\]](#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

Cuando se `CTypedPtrArray` utiliza `CPtrArray` `CObArray`en lugar de o , la función de comprobación de tipos C++ ayuda a eliminar los errores causados por tipos de puntero no coincidentes.

Además, `CTypedPtrArray` el contenedor realiza gran parte de la `CObArray` `CPtrArray`fundición que sería necesaria si se utiliza o .

Dado `CTypedPtrArray` que todas las funciones están en línea, el uso de esta plantilla no afecta significativamente al tamaño o la velocidad del código.

Para obtener más `CTypedPtrArray`información sobre el uso de , vea los artículos [Colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray::Add

Esta función `BASE_CLASS`miembro llama **a ::Add**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elemento que se agregará a la matriz.

*newElement*<br/>
El elemento que se va a agregar a esta matriz.

### <a name="return-value"></a>Valor devuelto

El índice del elemento agregado.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray::Append

Esta función `BASE_CLASS`miembro llama a ::Append**.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Clase base de la clase de matriz de puntero con tipo; debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

*src*<br/>
Origen de los elementos que se van a anexar a una matriz.

### <a name="return-value"></a>Valor devuelto

El índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray::Copy

Esta función `BASE_CLASS`miembro llama **a ::Copy**.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Clase base de la clase de matriz de puntero con tipo; debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

*src*<br/>
Origen de los elementos que se van a copiar en una matriz.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Esta función `BASE_CLASS`en línea llama **a ::ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro Template que especifica el tipo de elementos almacenados en esta matriz.

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `BASE_CLASS`menor o igual que el valor devuelto por **::GetUpperBound**.

### <a name="return-value"></a>Valor devuelto

Una referencia temporal al elemento en la ubicación especificada por *nIndex*. Este elemento es del tipo especificado por el parámetro de plantilla *TYPE*.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Esta función `BASE_CLASS`en línea llama **a ::GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la matriz.

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `BASE_CLASS`menor o igual que el valor devuelto por **::GetUpperBound**.

### <a name="return-value"></a>Valor devuelto

Una copia del elemento en la ubicación especificada por *nIndex*. Este elemento es del tipo especificado por el parámetro de plantilla *TYPE*.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, consulte [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Esta función `BASE_CLASS`miembro llama **a ::InsertAt**.

```
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que puede ser mayor que el valor devuelto por [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

*newElement*<br/>
El puntero de objeto que se va a colocar en esta matriz. Se permite *un newElement* de valor **NULL.**

*nCount*<br/>
El número de veces que se debe insertar este elemento (valor predeterminado es 1).

*nStartIndex*<br/>
Un índice entero que puede ser `CObArray::GetUpperBound`mayor que el valor devuelto por .

*BASE_CLASS*<br/>
Clase base de la clase de matriz de puntero con tipo; debe ser una clase de matriz ( [CObArray](../../mfc/reference/cobarray-class.md) o [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Otra matriz que contiene elementos que se agregarán a esta matriz.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray::operator [ ]

Estos operadores `BASE_CLASS`en línea llaman a **::operator [ ]**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la matriz.

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `BASE_CLASS`menor o igual que el valor devuelto por **::GetUpperBound**.

### <a name="remarks"></a>Observaciones

El primer operador, llamado para matrices que no son **const**, se puede utilizar en la derecha (valor r) o a la izquierda (valor l) de una instrucción de asignación. El segundo, invocado para las **matrices const,** solo se puede utilizar a la derecha.

La versión de depuración de la biblioteca afirma si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de los límites.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Esta función `BASE_CLASS`miembro llama **a ::SetAt**.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y menor o igual que el valor devuelto por [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

*Ptr*<br/>
Un puntero al elemento que se va a insertar en la matriz en el nIndex. Se permite un valor NULL.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Esta función `BASE_CLASS`miembro llama **a ::SetAtGrow**.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0.

*TIPO*<br/>
Tipo de los elementos almacenados en la matriz de clase base.

*newElement*<br/>
El puntero de objeto que se agregará a esta matriz. Se permite un valor **NULL.**

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Consulte también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray (clase)](../../mfc/reference/cptrarray-class.md)<br/>
[Clase CObArray](../../mfc/reference/cobarray-class.md)
