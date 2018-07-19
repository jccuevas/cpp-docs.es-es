---
title: CComSimpleThreadAllocator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2c571733aca48ddbfd881a294786d1de334c7c3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884670"
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
 *pApt*  
 No se utiliza en la implementación de predeterminada de ATL.  
  
 *nThreads*  
 El número máximo de subprocesos en el módulo del archivo EXE.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero entre cero y (*nThreads* - 1). Identifica uno de los subprocesos en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar `GetThread` para proporcionar un método de selección diferente o para hacer uso de la *pApt* parámetro.  
  
 `GetThread` llama a [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Vea también  
 [CComApartment (clase)](../../atl/reference/ccomapartment-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
