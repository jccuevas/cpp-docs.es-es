---
title: Clase CAutoVectorPtr
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
ms.openlocfilehash: 573446256aa89423837ebf73176a73f72054911b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318758"
---
# <a name="cautovectorptr-class"></a>Clase CAutoVectorPtr

Esta clase representa un objeto de puntero inteligente mediante vector new y delete operadores.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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

|Nombre|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|El constructor.|
|[CAutoVectorPtr::-CAutoVectorPtr](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::Asignar](#allocate)|Llame a este método para asignar la memoria `CAutoVectorPtr`requerida por la matriz de objetos a los que apunta .|
|[CAutoVectorPtr::Attach](#attach)|Llame a este método para tomar la propiedad de un puntero existente.|
|[CAutoVectorPtr::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CAutoVectorPtr::Gratis](#free)|Llame a este método para eliminar `CAutoVectorPtr`un objeto al que apunta un archivo .|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::operador T *](#operator_t__star)|El operador de colada.|
|[CAutoVectorPtr::operator ?](#operator_eq)|El operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|La variable miembro de datos de puntero.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para crear y administrar un puntero inteligente, que ayudará a proteger contra pérdidas de memoria liberando automáticamente los recursos cuando se queda fuera del ámbito. `CAutoVectorPtr`es similar `CAutoPtr`a , la `CAutoVectorPtr` única diferencia es que utiliza [vector new&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) y vector delete [&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) para asignar y liberar memoria en lugar de los operadores **new** y **delete** de C+++ . Consulte [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si `CAutoVectorPtr` se requieren clases de colección de.

Vea [CAutoPtr](../../atl/reference/cautoptr-class.md) para obtener un ejemplo del uso de una clase de puntero inteligente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Asignar

Llame a este método para asignar la memoria `CAutoVectorPtr`requerida por la matriz de objetos a los que apunta .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parámetros

*nElementos*<br/>
Número de elementos de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se asigna correctamente, false en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si la variable miembro [CAutoVectorPtr::m_p](#m_p) apunta actualmente a un valor existente; es decir, no es igual a NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Attach

Llame a este método para tomar la propiedad de un puntero existente.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
El `CAutoVectorPtr` objeto tomará la propiedad de este puntero.

### <a name="remarks"></a>Observaciones

Cuando `CAutoVectorPtr` un objeto toma la propiedad de un puntero, eliminará automáticamente el puntero y los datos asignados cuando salga del ámbito. Si se llama [a CAutoVectorPtr::Detach,](#detach) se vuelve a asignar al programador la responsabilidad de liberar los recursos asignados.

En compilaciones de depuración, se producirá un error de aserción si la variable miembro [CAutoVectorPtr::m_p](#m_p) apunta actualmente a un valor existente; es decir, no es igual a NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

El constructor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Un puntero existente.

### <a name="remarks"></a>Observaciones

El `CAutoVectorPtr` objeto se puede crear mediante un puntero existente, en cuyo caso transfiere la propiedad del puntero.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr::-CAutoVectorPtr

Destructor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados. Llama a [CAutoVectorPtr::Free](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Observaciones

Libera la propiedad de un puntero, establece la variable miembro [CAutoVectorPtr::m_p](#m_p) en NULL y devuelve una copia del puntero. Después `Detach`de llamar , depende del programador liberar `CAutoVectorPtr` los recursos asignados sobre los que el objeto puede haber asumido previamente la responsabilidad.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Gratis

Llame a este método para eliminar `CAutoVectorPtr`un objeto al que apunta un archivo .

```
void Free() throw();
```

### <a name="remarks"></a>Observaciones

El objeto al `CAutoVectorPtr` que apunta el se libera y el [CAutoVectorPtr::m_p](#m_p) variable miembro se establece en NULL.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr::m_p

La variable miembro de datos de puntero.

```
T* m_p;
```

### <a name="remarks"></a>Observaciones

Esta variable miembro contiene la información del puntero.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operator ?

El operador de asignación.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Un puntero.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un **CAutoVectorPtr\< T >**.

### <a name="remarks"></a>Observaciones

El operador de asignación separa el `CAutoVectorPtr` objeto de cualquier puntero actual y adjunta el nuevo puntero, *p*, en su lugar.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operador T *

El operador de colada.

```
operator T*() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.

## <a name="see-also"></a>Consulte también

[Clase CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
