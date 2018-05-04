---
title: Clase CComFakeCriticalSection | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a042e52439579cfb1b4145b1691f5a00128754c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 `CComFakeCriticalSection` refleja los métodos que se encuentra en [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComFakeCriticalSection` no proporciona una sección crítica; por lo tanto, sus métodos no hacen nada.  
  
 Normalmente, se utiliza `CComFakeCriticalSection` a través de un `typedef` nombre, ya sea `AutoCriticalSection` o `CriticalSection`. Cuando se usa [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ambos `typedef` nombres hagan referencia a `CComFakeCriticalSection`. Cuando se usa [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), hacen referencia a [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) y `CComCriticalSection`, respectivamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="init"></a>  CComFakeCriticalSection::Init  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="lock"></a>  CComFakeCriticalSection::Lock  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="term"></a>  CComFakeCriticalSection::Term  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock  
 No hace nada porque no hay ninguna sección crítica.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
