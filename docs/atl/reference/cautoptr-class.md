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
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321253"
---
# <a name="cautoptr-class"></a>Clase CAutoPtr

Esta clase representa un objeto de puntero inteligente.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|El constructor.|
|[CAutoPtr::-CAutoPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|Llame a este método para tomar la propiedad de un puntero existente.|
|[CAutoPtr::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CAutoPtr::Gratis](#free)|Llame a este método para eliminar `CAutoPtr`un objeto al que apunta un archivo .|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr::operador T*](#operator_t_star)|El operador de colada.|
|[CAutoPtr::operador ?](#operator_eq)|El operador de asignación.|
|[CAutoPtr::operator ->](#operator_ptr)|El operador de puntero a miembro.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|La variable miembro de datos de puntero.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para crear y administrar un puntero inteligente, que ayudará a proteger contra pérdidas de memoria liberando automáticamente los recursos cuando se queda fuera del ámbito.

Además, `CAutoPtr`el constructor de copia y el operador de asignación transfieren la propiedad del puntero, copiando el puntero de origen al puntero de destino y estableciendo el puntero de origen en NULL. Por lo tanto, `CAutoPtr` es imposible tener dos objetos cada uno almacenando el mismo puntero, y esto reduce la posibilidad de eliminar el mismo puntero dos veces.

`CAutoPtr`también simplifica la creación de colecciones de punteros. En lugar de derivar una clase de colección y reemplazar el `CAutoPtr` destructor, es más sencillo crear una colección de objetos. Cuando se elimina la `CAutoPtr` colección, los objetos saldrán del ámbito y se eliminarán automáticamente.

[CHeapPtr](../../atl/reference/cheapptr-class.md) y variantes funcionan de `CAutoPtr`la misma manera que , excepto que asignan y liberan memoria utilizando diferentes funciones de montón en lugar de los operadores **new** y **delete** de C+++ . [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) es `CAutoPtr`similar a , la única diferencia es que utiliza **vector new[]** y **vector delete[]** para asignar y liberar memoria.

Vea también [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) cuando se requieren matrices o listas de punteros inteligentes.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::Attach

Llame a este método para tomar la propiedad de un puntero existente.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
El `CAutoPtr` objeto tomará la propiedad de este puntero.

### <a name="remarks"></a>Observaciones

Cuando `CAutoPtr` un objeto toma la propiedad de un puntero, eliminará automáticamente el puntero y los datos asignados cuando salga del ámbito. Si se llama [a CAutoPtr::Detach,](#detach) se vuelve a asignar al programador la responsabilidad de liberar los recursos asignados.

En compilaciones de depuración, se producirá un error de aserción si el [CAutoPtr::m_p](#m_p) miembro de datos apunta actualmente a un valor existente; es decir, no es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

El constructor.

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Un puntero existente.

*TSrc*<br/>
El tipo que `CAutoPtr`está administrando otro , utilizado para inicializar el objeto actual.

### <a name="remarks"></a>Observaciones

El `CAutoPtr` objeto se puede crear mediante un puntero existente, en cuyo caso transfiere la propiedad del puntero.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr::-CAutoPtr

Destructor.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados. Llama a [CAutoPtr::Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Observaciones

Libera la propiedad de un puntero, establece la variable miembro de datos [CAutoPtr::m_p](#m_p) en NULL y devuelve una copia del puntero. Después `Detach`de llamar , depende del programador liberar `CAutoPtr` los recursos asignados sobre los que el objeto puede haber asumido previamente la responsabilidad.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr::Gratis

Llame a este método para eliminar `CAutoPtr`un objeto al que apunta un archivo .

```
void Free() throw();
```

### <a name="remarks"></a>Observaciones

El objeto al `CAutoPtr` que apunta el se libera y el [CAutoPtr::m_p](#m_p) variable miembro de datos se establece en NULL.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr::m_p

La variable miembro de datos de puntero.

```
T* m_p;
```

### <a name="remarks"></a>Observaciones

Esta variable miembro contiene la información del puntero.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::operador ?

El operador de asignación.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Un puntero.

*TSrc*<br/>
Un tipo de clase.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un **CAutoPtr\< T >**.

### <a name="remarks"></a>Observaciones

El operador de asignación separa el `CAutoPtr` objeto de cualquier puntero actual y adjunta el nuevo puntero, *p*, en su lugar.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr::operador -&gt;

El operador de puntero a miembro.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la [CAutoPtr::m_p](#m_p) variable miembro de datos.

### <a name="remarks"></a>Observaciones

Utilice este operador para llamar a un `CAutoPtr` método en una clase señalada por el objeto. En compilaciones de depuración, se `CAutoPtr` producirá un error de aserción si el punto null.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::operador T*

El operador de colada.

```
operator T* () const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.

### <a name="example"></a>Ejemplo

Vea el ejemplo en La descripción general de [CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Consulte también

[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
