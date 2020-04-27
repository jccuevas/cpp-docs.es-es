---
title: Clase CAutoPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 7f15e16b075b9a5327723a7f081100313f14ea77
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167726"
---
# <a name="cautoptr-class"></a>Clase CAutoPtr

Esta clase representa un objeto de puntero inteligente.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de puntero.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|El constructor.|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr:: Attach](#attach)|Llame a este método para tomar posesión de un puntero existente.|
|[CAutoPtr::D Etach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CAutoPtr:: Free](#free)|Llame a este método para eliminar un objeto al que apunta `CAutoPtr`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr:: Operator T *](#operator_t_star)|Operador de conversión.|
|[CAutoPtr:: Operator =](#operator_eq)|Operador de asignación.|
|[CAutoPtr:: Operator->](#operator_ptr)|Operador de puntero a miembro.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr:: m_p](#m_p)|Variable de miembro de datos de puntero.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para crear y administrar un puntero inteligente, que ayudará a protegerse frente a pérdidas de memoria liberando automáticamente los recursos cuando se queda fuera del ámbito.

Además, `CAutoPtr`el constructor de copias y el operador de asignación transfieren la propiedad del puntero, copiando el puntero de origen en el puntero de destino y estableciendo el puntero de origen en NULL. Por lo tanto, no es posible `CAutoPtr` tener dos objetos que almacenen el mismo puntero, lo que reduce la posibilidad de eliminar el mismo puntero dos veces.

`CAutoPtr`también simplifica la creación de colecciones de punteros. En lugar de derivar una clase de colección e invalidar el destructor, es más sencillo crear una colección de `CAutoPtr` objetos. Cuando se elimina la colección, los `CAutoPtr` objetos salen del ámbito y se eliminan automáticamente.

[CHeapPtr](../../atl/reference/cheapptr-class.md) y las variantes funcionan de la misma manera `CAutoPtr`que, salvo que asignan y liberan memoria mediante distintas funciones del montón en lugar de los operadores **New** y **Delete** de C++. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) es similar a `CAutoPtr`, la única diferencia es que usa **Vector New []** y **Vector delete []** para asignar y liberar memoria.

Vea también [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) cuando se requieren matrices o listas de punteros inteligentes.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr:: Attach

Llame a este método para tomar posesión de un puntero existente.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parámetros

*m*<br/>
El `CAutoPtr` objeto tomará posesión de este puntero.

### <a name="remarks"></a>Observaciones

Cuando un `CAutoPtr` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando salga del ámbito. Si se llama a [CAutoPtr::D Etach](#detach) , el programador vuelve a tener la responsabilidad de liberar los recursos asignados.

En las compilaciones de depuración, se producirá un error de aserción si el miembro de datos [CAutoPtr:: m_p](#m_p) apunta actualmente a un valor existente; es decir, no es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

El constructor.

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*m*<br/>
Un puntero existente.

*TSrc*<br/>
Tipo administrado por otro `CAutoPtr`que se usa para inicializar el objeto actual.

### <a name="remarks"></a>Observaciones

El `CAutoPtr` objeto se puede crear con un puntero existente, en cuyo caso transfiere la propiedad del puntero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr:: ~ CAutoPtr

Destructor.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados. Llama a [CAutoPtr:: Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::D Etach

Llame a este método para liberar la propiedad de un puntero.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Observaciones

Libera la propiedad de un puntero, establece la variable de miembro de datos [CAutoPtr:: m_p](#m_p) en NULL y devuelve una copia del puntero. Después de `Detach`llamar a, depende del programador liberar los recursos asignados a través de los `CAutoPtr` que el objeto puede haber asumido reponsibility previamente.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr:: Free

Llame a este método para eliminar un objeto al que apunta `CAutoPtr`.

```cpp
void Free() throw();
```

### <a name="remarks"></a>Observaciones

El objeto al que apunta `CAutoPtr` se libera y la variable de miembro de datos [CAutoPtr:: m_p](#m_p) está establecida en NULL.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr:: m_p

Variable de miembro de datos de puntero.

```cpp
T* m_p;
```

### <a name="remarks"></a>Observaciones

Esta variable miembro contiene la información del puntero.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr:: Operator =

Operador de asignación.

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parámetros

*m*<br/>
Puntero.

*TSrc*<br/>
Tipo de clase.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un **>\< CAutoPtr T **.

### <a name="remarks"></a>Observaciones

El operador de asignación desasocia `CAutoPtr` el objeto de cualquier puntero actual y asocia el nuevo puntero, *p*, en su lugar.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr:: Operator-&gt;

Operador de puntero a miembro.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la variable de miembro de datos [CAutoPtr:: m_p](#m_p) .

### <a name="remarks"></a>Observaciones

Utilice este operador para llamar a un método en una clase a la que `CAutoPtr` apunta el objeto. En las `CAutoPtr` compilaciones de depuración, se producirá un error de aserción si apunta a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr:: Operator T *

Operador de conversión.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al tipo de datos del objeto definido en la plantilla de clase.

### <a name="example"></a>Ejemplo

Vea el ejemplo de la [información general de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Consulte también

[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
