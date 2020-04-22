---
title: Clase CHeapPtrBase
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: e247b4f488411ffdcde5d1d9016436c9c36fe793
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747688"
---
# <a name="cheapptrbase-class"></a>Clase CHeapPtrBase

Esta clase forma la base para varias clases de puntero de montón inteligente.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se va a almacenar en el montón.

*Asignador*<br/>
La clase de asignación de memoria que se va a utilizar. De forma predeterminada, las rutinas de CRT se utilizan para asignar y liberar memoria.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrBase::-CheapPtrBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Llame a este método para asignar memoria.|
|[CHeapPtrBase::Attach](#attach)|Llame a este método para tomar la propiedad de un puntero existente.|
|[CHeapPtrBase::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CHeapPtrBase::Gratis](#free)|Llame a este método para eliminar `CHeapPtrBase`un objeto al que apunta un archivo .|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Llame a este método para reasignar memoria.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrBase::operador T*](#operator_t_star)|El operador de colada.|
|[CHeapPtrBase::operator &](#operator_amp)|El operador &.|
|[CHeapPtrBase::operator ->](#operator_ptr)|El operador de puntero a miembro.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|La variable miembro de datos de puntero.|

## <a name="remarks"></a>Observaciones

Esta clase forma la base para varias clases de puntero de montón inteligente. Las clases derivadas, por ejemplo, [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), agregan sus propios constructores y operadores. Consulte estas clases para obtener ejemplos de implementación.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes

Llame a este método para asignar memoria.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
El número de bytes de memoria que se van a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se asigna correctamente, false en caso contrario.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si la variable miembro [CHeapPtrBase::m_pData](#m_pdata) apunta actualmente a un valor existente; es decir, no es igual a NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase::Attach

Llame a este método para tomar la propiedad de un puntero existente.

```cpp
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
El `CHeapPtrBase` objeto tomará la propiedad de este puntero.

### <a name="remarks"></a>Observaciones

Cuando `CHeapPtrBase` un objeto toma la propiedad de un puntero, eliminará automáticamente el puntero y los datos asignados cuando salga del ámbito.

En compilaciones de depuración, se producirá un error de aserción si la variable miembro [CHeapPtrBase::m_pData](#m_pdata) apunta actualmente a un valor existente; es decir, no es igual a NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase::-CheapPtrBase

Destructor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Observaciones

Libera la propiedad de un puntero, establece el [CHeapPtrBase::m_pData](#m_pdata) variable miembro en NULL y devuelve una copia del puntero.

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase::Gratis

Llame a este método para eliminar `CHeapPtrBase`un objeto al que apunta un archivo .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Observaciones

El objeto al `CHeapPtrBase` que apunta el se libera y el [CHeapPtrBase::m_pData](#m_pdata) variable miembro se establece en NULL.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase::m_pData

La variable miembro de datos de puntero.

```
T* m_pData;
```

### <a name="remarks"></a>Observaciones

Esta variable miembro contiene la información del puntero.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::operator&amp;

El operador &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del objeto `CHeapPtrBase` al que apunta el objeto.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase::operador -&gt;

El operador de puntero a miembro.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la [CHeapPtrBase::m_pData](#m_pdata) variable miembro.

### <a name="remarks"></a>Observaciones

Utilice este operador para llamar a un `CHeapPtrBase` método en una clase señalada por el objeto. En compilaciones de depuración, se `CHeapPtrBase` producirá un error de aserción si el punto null.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase::operador T*

El operador de colada.

```
operator T*() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve [CHeapPtrBase::m_pData](#m_pdata).

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes

Llame a este método para reasignar memoria.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
La nueva cantidad de memoria que se va a asignar, en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria se asigna correctamente, false en caso contrario.

## <a name="see-also"></a>Vea también

[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
