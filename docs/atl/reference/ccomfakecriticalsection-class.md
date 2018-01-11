---
title: Clase CComFakeCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs: C++
helpviewer_keywords: CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b9f7b3b56193100d21ef7aebaba0ab6d9ecfd5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomfakecriticalsection-class"></a>Clase CComFakeCriticalSection
Esta clase proporciona los mismos métodos que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pero no proporciona una sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Lock](#lock)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Term](#term)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Unlock](#unlock)|No hace nada porque no hay ninguna sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 `CComFakeCriticalSection`refleja los métodos que se encuentra en [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComFakeCriticalSection` no proporciona una sección crítica; por lo tanto, sus métodos no hacen nada.  
  
 Normalmente, se utiliza `CComFakeCriticalSection` a través de un `typedef` nombre, ya sea `AutoCriticalSection` o `CriticalSection`. Cuando se usa [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ambos `typedef` nombres hagan referencia a `CComFakeCriticalSection`. Cuando se usa [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), hacen referencia a [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) y `CComCriticalSection`, respectivamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="init"></a>CComFakeCriticalSection::Init  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="lock"></a>CComFakeCriticalSection::Lock  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="term"></a>CComFakeCriticalSection::Term  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="unlock"></a>CComFakeCriticalSection::Unlock  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
