---
title: Clase CComCritSecLock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 71b9ab8b11adc946656c2192c2f0f06555ef1254
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcritseclock-class"></a>Clase CComCritSecLock
Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>Parámetros  
 *TLock*  
 El objeto de bloqueo y desbloqueado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|El constructor.|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|Llame a este método para bloquear el objeto de sección crítica.|  
|[CComCritSecLock::Unlock](#unlock)|Llame a este método para desbloquear el objeto de sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta clase para bloquear y desbloquear objetos de un modo más seguro que con la [clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) o [CComAutoCriticalSection clase](../../atl/reference/ccomautocriticalsection-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 El constructor.  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 El objeto de sección crítica.  
  
 `bInitialLock`  
 El estado de bloqueo inicial: **true** significa bloqueado.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el objeto de sección crítica.  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 Destructor.  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Desbloquea el objeto de sección crítica.  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 Llame a este método para bloquear el objeto de sección crítica.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ha bloqueado correctamente el objeto, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto ya está bloqueado, se producirá un error de aserción en compilaciones de depuración.  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 Llame a este método para desbloquear el objeto de sección crítica.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto ya está desbloqueado, se producirá un error de aserción en compilaciones de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Clase CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)

