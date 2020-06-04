---
title: Clase CComSimpleThreadAllocator
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327346"
---
# <a name="ccomsimplethreadallocator-class"></a>Clase CComSimpleThreadAllocator

Esta clase administra la `CComAutoThreadModule`selección de subprocesos para la clase.

## <a name="syntax"></a>Sintaxis

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Selecciona un subproceso.|

## <a name="remarks"></a>Observaciones

`CComSimpleThreadAllocator`administra la selección de subprocesos para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`simplemente recorre cada subproceso y devuelve el siguiente en la secuencia.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleThreadAllocator::GetThread

Selecciona un subproceso especificando el siguiente subproceso de la secuencia.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parámetros

*pApt*<br/>
No se utiliza en la implementación predeterminada de ATL.

*nThreads*<br/>
El número máximo de subprocesos en el módulo EXE.

### <a name="return-value"></a>Valor devuelto

Un entero entre cero y (*nThreads* - 1). Identifica uno de los subprocesos del módulo EXE.

### <a name="remarks"></a>Observaciones

Puede reemplazar `GetThread` para proporcionar un método diferente de selección o para hacer uso del parámetro *pApt.*

`GetThread`es llamado por [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Consulte también

[Clase CComApartment](../../atl/reference/ccomapartment-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
