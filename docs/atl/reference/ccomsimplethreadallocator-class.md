---
title: CComSimpleThreadAllocator (clase)
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
ms.openlocfilehash: 1644014048b27b7ab6076783c5025140527a7ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637546"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator (clase)

Esta clase administra la selección de subproceso para la clase `CComAutoThreadModule`.

## <a name="syntax"></a>Sintaxis

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Selecciona un subproceso.|

## <a name="remarks"></a>Comentarios

`CComSimpleThreadAllocator` administra la selección de subproceso para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` simplemente recorre cada subproceso y devuelve el siguiente en la secuencia.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

Selecciona un subproceso especificando el siguiente subproceso en la secuencia.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parámetros

*pApt*<br/>
No se utiliza en la implementación de predeterminada de ATL.

*nThreads*<br/>
El número máximo de subprocesos en el módulo del archivo EXE.

### <a name="return-value"></a>Valor devuelto

Un entero entre cero y (*nThreads* - 1). Identifica uno de los subprocesos en el módulo del archivo EXE.

### <a name="remarks"></a>Comentarios

Puede invalidar `GetThread` para proporcionar un método de selección diferente o para hacer uso de la *pApt* parámetro.

`GetThread` llama a [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Vea también

[CComApartment (clase)](../../atl/reference/ccomapartment-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
