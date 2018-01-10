---
title: Clase CComSimpleThreadAllocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 244443692478d0391c2079e55995c1fef1e1655e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsimplethreadallocator-class"></a>Clase CComSimpleThreadAllocator
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
 `CComSimpleThreadAllocator`administra la selección de subproceso para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`simplemente recorre cada subproceso y devuelve el siguiente en la secuencia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 Selecciona un subproceso especificando el siguiente subproceso de la secuencia.  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `pApt`  
 No se utiliza en la implementación predeterminada de ATL.  
  
 `nThreads`  
 El número máximo de subprocesos en el módulo del archivo EXE.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero comprendido entre cero y ( `nThreads` - 1). Identifica uno de los subprocesos en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar `GetThread` para proporcionar un método diferente de la selección o para hacer uso de la `pApt` parámetro.  
  
 `GetThread`llama a [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Vea también  
 [Clase CComApartment](../../atl/reference/ccomapartment-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
