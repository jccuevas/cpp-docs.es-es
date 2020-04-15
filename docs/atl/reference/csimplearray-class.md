---
title: Clase CSimpleArray
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: e45c9b3fd778aacd3a3e2d5d3696661afa0c6fb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330910"
---
# <a name="csimplearray-class"></a>Clase CSimpleArray

Esta clase proporciona métodos para administrar una matriz simple.

## <a name="syntax"></a>Sintaxis

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la matriz.

*TEqual*<br/>
Un objeto de rasgo, que define la prueba de igualdad para elementos de tipo *T*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|El constructor de la matriz simple.|
|[CSimpleArray::-CSimpleArray](#dtor)|El destructor de la matriz simple.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleArray::Add](#add)|Agrega un nuevo elemento a la matriz.|
|[CSimpleArray::Buscar](#find)|Busca un elemento en la matriz.|
|[CSimpleArray::GetData](#getdata)|Devuelve un puntero a los datos almacenados en la matriz.|
|[CSimpleArray::GetSize](#getsize)|Devuelve el número de elementos almacenados en la matriz.|
|[CSimpleArray::Remove](#remove)|Quita un elemento determinado de la matriz.|
|[CSimpleArray::RemoveAll](#removeall)|Quita todos los elementos de la matriz.|
|[CSimpleArray::RemoveAt](#removeat)|Quita el elemento especificado de la matriz.|
|[CSimpleArray::SetAtIndex](#setatindex)|Establece el elemento especificado en la matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Recupera un elemento de la matriz.|
|[CSimpleArray::operador ?](#operator_eq)|Operador de asignación.|

## <a name="remarks"></a>Observaciones

`CSimpleArray`proporciona métodos para crear y administrar una `T`matriz simple, de cualquier tipo dado.

El `TEqual` parámetro proporciona un medio para definir una función de igualdad para dos elementos de tipo `T`. Al crear una clase similar a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz determinada. Por ejemplo, cuando se trata de una matriz de punteros, puede ser útil definir la igualdad como en función de los valores a los que hacen referencia los punteros. La implementación por defecto utiliza **operator()**.

Tanto `CSimpleArray` [CSimpleMap como CSimpleMap](../../atl/reference/csimplemap-class.md) están diseñados para un pequeño número de elementos. [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md) se deben utilizar cuando la matriz contiene un gran número de elementos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>CSimpleArray::Add

Agrega un nuevo elemento a la matriz.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El elemento que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento se agrega correctamente a la matriz, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>CSimpleArray::CSimpleArray

El constructor del objeto de matriz.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Objeto `CSimpleArray` existente.

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos, creando un nuevo objeto vacío `CSimpleArray` o una copia de un objeto existente. `CSimpleArray`

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>CSimpleArray::-CSimpleArray

Destructor.

```
~CSimpleArray();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="csimplearrayfind"></a><a name="find"></a>CSimpleArray::Buscar

Busca un elemento en la matriz.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El elemento para el que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del elemento encontrado, o -1 si no se encuentra el elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimpleArray::GetData

Devuelve un puntero a los datos almacenados en la matriz.

```
T* GetData() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a los datos de la matriz.

## <a name="csimplearraygetsize"></a><a name="getsize"></a>CSimpleArray::GetSize

Devuelve el número de elementos almacenados en la matriz.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos almacenados en la matriz.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::operator\[\]

Recupera un elemento de la matriz.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento de la matriz a la que hace referencia *nIndex*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::operador ?

Operador de asignación.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Matriz que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `CSimpleArray` al objeto actualizado.

### <a name="remarks"></a>Observaciones

Copia todos los `CSimpleArray` elementos del objeto al que hace referencia *src* en el objeto de matriz actual, reemplazando todos los datos existentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>CSimpleArray::Remove

Quita un elemento determinado de la matriz.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El elemento que se va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se encuentra y quita el elemento, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Cuando se quita un elemento, los elementos restantes de la matriz se vuelven a numerar para rellenar el espacio vacío.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>CSimpleArray::RemoveAll

Quita todos los elementos de la matriz.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Quita todos los elementos almacenados actualmente en la matriz.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>CSimpleArray::RemoveAt

Quita el elemento especificado de la matriz.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice que apunta al elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se quitó el elemento, FALSE si el índice no era válido.

### <a name="remarks"></a>Observaciones

Cuando se quita un elemento, los elementos restantes de la matriz se vuelven a numerar para rellenar el espacio vacío.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>CSimpleArray::SetAtIndex

Establezca el elemento especificado en la matriz.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del elemento que se va a cambiar.

*T*<br/>
El valor que se va a asignar al elemento especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente, FALSE si el índice no era válido.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
