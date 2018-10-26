---
title: CSimpleArray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03f4161130a1517bba6ed87164a814a9e8c61bbd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069729"
---
# <a name="csimplearray-class"></a>CSimpleArray (clase)

Esta clase proporciona métodos para administrar una matriz simple.

## <a name="syntax"></a>Sintaxis

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se va a almacenar en la matriz.

*TEqual*<br/>
Un objeto de rasgo, definiendo la prueba de igualdad para los elementos de tipo *T*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|El constructor de la matriz simple.|
|[CSimpleArray:: ~ CSimpleArray](#dtor)|El destructor para la matriz simple.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleArray::Add](#add)|Agrega un nuevo elemento a la matriz.|
|[CSimpleArray::Find](#find)|Busca un elemento de la matriz.|
|[CSimpleArray::GetData](#getdata)|Devuelve un puntero a los datos almacenados en la matriz.|
|[CSimpleArray::GetSize](#getsize)|Devuelve el número de elementos almacenados en la matriz.|
|[CSimpleArray::Remove](#remove)|Quita un elemento determinado de la matriz.|
|[CSimpleArray::RemoveAll](#removeall)|Quita todos los elementos de la matriz.|
|[CSimpleArray::RemoveAt](#removeat)|Quita el elemento especificado de la matriz.|
|[CSimpleArray::SetAtIndex](#setatindex)|Establece el elemento especificado de la matriz.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Recupera un elemento de la matriz.|
|[CSimpleArray::operator =](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Comentarios

`CSimpleArray` Proporciona métodos para crear y administrar la matriz de cualquier tipo simple, `T`.

El parámetro `TEqual` proporciona un medio para definir una función de igualdad para los dos elementos de tipo `T`. Mediante la creación de una clase similar a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz determinado. Por ejemplo, cuando se trabaja con una matriz de punteros, puede ser útil definir la igualdad como función de los valores que hacen referencia a los punteros. La implementación predeterminada usa **operator=()**.

Ambos `CSimpleArray` y [CSimpleMap](../../atl/reference/csimplemap-class.md) están diseñados para un pequeño número de elementos. [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md) debe usarse cuando la matriz contiene un gran número de elementos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

##  <a name="add"></a>  CSimpleArray::Add

Agrega un nuevo elemento a la matriz.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
Elemento que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento se agrega correctamente a la matriz, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray

El constructor para el objeto de matriz.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Objeto `CSimpleArray` existente.

### <a name="remarks"></a>Comentarios

Inicializa los miembros de datos, crear una nueva y vacía `CSimpleArray` objeto o una copia de una existente `CSimpleArray` objeto.

##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray

Destructor.

```
~CSimpleArray();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="find"></a>  CSimpleArray::Find

Busca un elemento de la matriz.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Parámetros

*t*<br/>
El elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del elemento encontrado, o -1 si no se encuentra el elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

##  <a name="getdata"></a>  CSimpleArray::GetData

Devuelve un puntero a los datos almacenados en la matriz.

```
T* GetData() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a los datos de la matriz.

##  <a name="getsize"></a>  CSimpleArray::GetSize

Devuelve el número de elementos almacenados en la matriz.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos almacenados en la matriz.

##  <a name="operator_at"></a>  CSimpleArray::operator \[\]

Recupera un elemento de la matriz.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento de la matriz al que hace referencia *nIndex*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

##  <a name="operator_eq"></a>  CSimpleArray::operator =

Operador de asignación.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Para copiar la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la actualización `CSimpleArray` objeto.

### <a name="remarks"></a>Comentarios

Copia todos los elementos de la `CSimpleArray` hacen referencia al objeto *src* en el objeto de matriz actual, reemplazar todos los datos existentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

##  <a name="remove"></a>  CSimpleArray::Remove

Quita un elemento determinado de la matriz.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Parámetros

*t*<br/>
Elemento que se va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento se encuentra y quita, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Cuando se quita un elemento, se vuelven a numerar los elementos restantes de la matriz para rellenar el espacio vacío.

##  <a name="removeall"></a>  CSimpleArray::RemoveAll

Quita todos los elementos de la matriz.

```
void RemoveAll();
```

### <a name="remarks"></a>Comentarios

Quita todos los elementos almacenados actualmente en la matriz.

##  <a name="removeat"></a>  CSimpleArray::RemoveAt

Quita el elemento especificado de la matriz.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice que apunta al elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento se quitó, FALSE si el índice no era válido.

### <a name="remarks"></a>Comentarios

Cuando se quita un elemento, se vuelven a numerar los elementos restantes de la matriz para rellenar el espacio vacío.

##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex

Establezca el elemento especificado de la matriz.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento que se va a cambiar.

*t*<br/>
El valor que se va a asignar al elemento especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente, FALSE si el índice no era válido.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
