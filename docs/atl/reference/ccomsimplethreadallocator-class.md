---
title: Clase CComSimpleThreadAllocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 377e7f2fa6d8377d46e98b52e9c8f075b10956a8
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsimplethreadallocator-class"></a>Clase CComSimpleThreadAllocator
Esta clase administra la selección de subproceso para la clase `CComAutoThreadModule`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|Selecciona un subproceso.|  
  
## <a name="remarks"></a>Comentarios  
 `CComSimpleThreadAllocator`administra la selección de subproceso para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`simplemente recorre cada subproceso y devuelve el siguiente en la secuencia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 Selecciona un subproceso especificando el siguiente subproceso en la secuencia.  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `pApt`  
 No se utiliza en la implementación predeterminada ATL.  
  
 `nThreads`  
 El número máximo de subprocesos en el módulo del archivo EXE.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero entre cero y ( `nThreads` – 1). Identifica uno de los subprocesos en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar `GetThread` para proporcionar un método diferente de la selección o para hacer uso de la `pApt` parámetro.  
  
 `GetThread`llama a [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Vea también  
 [Clase CComApartment](../../atl/reference/ccomapartment-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

