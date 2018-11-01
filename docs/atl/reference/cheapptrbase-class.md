---
title: CHeapPtrBase (clase)
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
ms.openlocfilehash: f183bb21d6a23b4e8ac4284894cfa2fcc7bb1dfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538165"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase (clase)

Esta clase constituye la base de varias clases de puntero inteligente de montón.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se almacenará en el montón.

*Asignador*<br/>
La clase de asignación de memoria que utilice. De forma predeterminada, las rutinas de CRT se usan para asignar y liberar memoria.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Llame a este método para asignar memoria.|
|[CHeapPtrBase::Attach](#attach)|Llame a este método para tomar posesión de un puntero existente.|
|[CHeapPtrBase::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CHeapPtrBase::Free](#free)|Llame a este método para eliminar un objeto al que señala un `CHeapPtrBase`.|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Llame a este método para reasignar memoria.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrBase::operator T *](#operator_t_star)|El operador de conversión.|
|[CHeapPtrBase::operator &](#operator_amp)|El & operador.|
|[CHeapPtrBase::operator ->](#operator_ptr)|El operador de puntero a miembro.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|La variable de miembro de datos de puntero.|

## <a name="remarks"></a>Comentarios

Esta clase constituye la base de varias clases de puntero inteligente de montón. Las clases derivadas, por ejemplo, [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), agregar sus propios constructores y operadores. Vea estas clases para obtener ejemplos de implementación.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes

Llame a este método para asignar memoria.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
El número de bytes de memoria para asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria está correctamente asignada, false en caso contrario.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si el [CHeapPtrBase::m_pData](#m_pdata) variable miembro apunta actualmente a un valor existente; es decir, no es igual a NULL.

##  <a name="attach"></a>  CHeapPtrBase::Attach

Llame a este método para tomar posesión de un puntero existente.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
La `CHeapPtrBase` objeto tomará posesión de este puntero.

### <a name="remarks"></a>Comentarios

Cuando un `CHeapPtrBase` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito.

En las compilaciones de depuración, se producirá un error de aserción si el [CHeapPtrBase::m_pData](#m_pdata) variable miembro apunta actualmente a un valor existente; es decir, no es igual a NULL.

##  <a name="dtor"></a>  CHeapPtrBase:: ~ CHeapPtrBase

Destructor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="detach"></a>  CHeapPtrBase::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Comentarios

Libera la propiedad de un puntero, Establece el [CHeapPtrBase::m_pData](#m_pdata) variable miembro en NULL y devuelve una copia del puntero.

##  <a name="free"></a>  CHeapPtrBase::Free

Llame a este método para eliminar un objeto al que señala un `CHeapPtrBase`.

```
void Free() throw();
```

### <a name="remarks"></a>Comentarios

El objeto que apunta el `CHeapPtrBase` se libera y el [CHeapPtrBase::m_pData](#m_pdata) variable miembro se establece en NULL.

##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData

La variable de miembro de datos de puntero.

```
T* m_pData;
```

### <a name="remarks"></a>Comentarios

Esta variable miembro contiene la información de puntero.

##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;

El & operador.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del objeto que apunta el `CHeapPtrBase` objeto.

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator-&gt;

El operador de puntero a miembro.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la [CHeapPtrBase::m_pData](#m_pdata) variable miembro.

### <a name="remarks"></a>Comentarios

Utilice este operador para llamar a un método en una clase que apunta el `CHeapPtrBase` objeto. En las compilaciones de depuración, se producirá un error de aserción si el `CHeapPtrBase` apunta a NULL.

##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *

El operador de conversión.

```
operator T*() const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve [CHeapPtrBase::m_pData](#m_pdata).

##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes

Llame a este método para reasignar memoria.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
La nueva cantidad de memoria para asignar, en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve true si la memoria está correctamente asignada, false en caso contrario.

## <a name="see-also"></a>Vea también

[CHeapPtr (clase)](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr (clase)](../../atl/reference/ccomheapptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
