---
title: CAutoVectorPtr (clase)
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: f614318125f3c6bce4003fee5fb4a945c7c88129
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259560"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr (clase)

Esta clase representa un objeto de puntero inteligente con nuevo vector y elimina operadores.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|El constructor.|
|[CAutoVectorPtr::~CAutoVectorPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::Allocate](#allocate)|Llame a este método para asignar la memoria requerida por la matriz de objetos que apunta `CAutoVectorPtr`.|
|[CAutoVectorPtr::Attach](#attach)|Llame a este método para tomar posesión de un puntero existente.|
|[CAutoVectorPtr::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CAutoVectorPtr::Free](#free)|Llame a este método para eliminar un objeto al que señala un `CAutoVectorPtr`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|El operador de conversión.|
|[CAutoVectorPtr::operator =](#operator_eq)|El operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|La variable de miembro de datos de puntero.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos para crear y administrar un puntero inteligente, que le ayudarán a proteger frente a pérdidas de memoria por los recursos se liberan automáticamente cuando se encuentra fuera del ámbito. `CAutoVectorPtr` es similar a `CAutoPtr`, la única diferencia es que `CAutoVectorPtr` usa [nuevo vector&#91; &#93; ](../../standard-library/new-operators.md#op_new_arr) y [vector delete&#91; &#93; ](../../standard-library/new-operators.md#op_delete_arr) para asignar y liberar memoria en lugar de C++ **nueva** y **eliminar** operadores. Consulte [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si las clases de colección de `CAutoVectorPtr` son necesarios.

Consulte [CAutoPtr](../../atl/reference/cautoptr-class.md) para obtener un ejemplo del uso de una clase de puntero inteligente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="allocate"></a>  CAutoVectorPtr::Allocate

Llame a este método para asignar la memoria requerida por la matriz de objetos que apunta `CAutoVectorPtr`.

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parámetros

*nElements*<br/>
Número de elementos de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria está correctamente asignada, false en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si el [CAutoVectorPtr::m_p](#m_p) variable miembro apunta actualmente a un valor existente; es decir, no es igual a NULL.

##  <a name="attach"></a>  CAutoVectorPtr::Attach

Llame a este método para tomar posesión de un puntero existente.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
La `CAutoVectorPtr` objeto tomará posesión de este puntero.

### <a name="remarks"></a>Comentarios

Cuando un `CAutoVectorPtr` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito. Si [CAutoVectorPtr::Detach](#detach) es llama, el programador se vuelva a dada la responsabilidad para liberar cualquier asigna los recursos.

En las compilaciones de depuración, se producirá un error de aserción si el [CAutoVectorPtr::m_p](#m_p) variable miembro apunta actualmente a un valor existente; es decir, no es igual a NULL.

##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr

El constructor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Un puntero existente.

### <a name="remarks"></a>Comentarios

La `CAutoVectorPtr` objeto puede crearse mediante un puntero existente, en cuyo caso transfiere la propiedad del puntero.

##  <a name="dtor"></a>  CAutoVectorPtr::~CAutoVectorPtr

Destructor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados. Las llamadas [CAutoVectorPtr::Free](#free).

##  <a name="detach"></a>  CAutoVectorPtr::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Comentarios

Libera la propiedad de un puntero, Establece el [CAutoVectorPtr::m_p](#m_p) variable miembro en NULL y devuelve una copia del puntero. Después de llamar a `Detach`, es hasta el programador para liberarlos recursos asignado en el que el `CAutoVectorPtr` objeto puede haber supuesto previamente responsabilidad.

##  <a name="free"></a>  CAutoVectorPtr::Free

Llame a este método para eliminar un objeto al que señala un `CAutoVectorPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Comentarios

El objeto que apunta el `CAutoVectorPtr` se libera y el [CAutoVectorPtr::m_p](#m_p) variable miembro se establece en NULL.

##  <a name="m_p"></a>  CAutoVectorPtr::m_p

La variable de miembro de datos de puntero.

```
T* m_p;
```

### <a name="remarks"></a>Comentarios

Esta variable miembro contiene la información de puntero.

##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =

El operador de asignación.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Un puntero.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un **CAutoVectorPtr\< T >**.

### <a name="remarks"></a>Comentarios

El operador de asignación se separa la `CAutoVectorPtr` objeto desde el puntero actual y asocia el nuevo puntero, *p*, en su lugar.

##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *

El operador de conversión.

```
operator T*() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.

## <a name="see-also"></a>Vea también

[CAutoPtr (clase)](../../atl/reference/cautoptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
