---
title: Clase CComFakeCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327856"
---
# <a name="ccomfakecriticalsection-class"></a>Clase CComFakeCriticalSection

Esta clase proporciona los mismos métodos que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pero no proporciona una sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComFakeCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|No hace nada ya que no hay una sección crítica.|
|[CComFakeCriticalSection::Lock](#lock)|No hace nada ya que no hay una sección crítica.|
|[CComFakeCriticalSection::Term](#term)|No hace nada ya que no hay una sección crítica.|
|[CComFakeCriticalSection::Unlock](#unlock)|No hace nada ya que no hay una sección crítica.|

## <a name="remarks"></a>Observaciones

`CComFakeCriticalSection`refleja los métodos encontrados en [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin `CComFakeCriticalSection` embargo, no proporciona una sección crítica; por lo tanto, sus métodos no hacen nada.

Normalmente, se `CComFakeCriticalSection` usa `typedef` a `AutoCriticalSection` través de un nombre, ya sea o `CriticalSection`. Cuando se usa [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ambos `typedef` nombres hacen referencia `CComFakeCriticalSection`. Cuando se usa [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), hacen `CComCriticalSection`referencia a [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) y , respectivamente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSection::Init

No hace nada ya que no hay una sección crítica.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSection::Lock

No hace nada ya que no hay una sección crítica.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSection::Term

No hace nada ya que no hay una sección crítica.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSection::Unlock

No hace nada ya que no hay una sección crítica.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
