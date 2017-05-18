---
title: Clase CComFakeCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 2c1269288e03a8ac9f359dad9acf1a81ddbc84c2
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[CComFakeCriticalSection::Init](#init)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Lock](#lock)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Term](#term)|No hace nada porque no hay ninguna sección crítica.|  
|[CComFakeCriticalSection::Unlock](#unlock)|No hace nada porque no hay ninguna sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 `CComFakeCriticalSection`refleja los métodos de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Sin embargo, `CComFakeCriticalSection` no proporciona una sección crítica; por lo tanto, sus métodos no hacen nada.  
  
 Normalmente, se utiliza `CComFakeCriticalSection` a través de un `typedef` nombre, ya sea `AutoCriticalSection` o `CriticalSection`. Al usar [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ambos `typedef` nombres hagan referencia a `CComFakeCriticalSection`. Al usar [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), hacen referencia a [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) y `CComCriticalSection`, respectivamente.  
  
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
 [Información general de la clase](../../atl/atl-class-overview.md)

