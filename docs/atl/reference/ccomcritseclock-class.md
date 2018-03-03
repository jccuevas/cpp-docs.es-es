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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cb07c2cca9394c23c6c3db156e205749f62e3f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcritseclock-class"></a>Clase CComCritSecLock
Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>Parámetros  
 *TLock*  
 El objeto se bloquea y desbloquea.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|El constructor.|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|Llame a este método para bloquear el objeto de sección crítica.|  
|[CComCritSecLock::Unlock](#unlock)|Llamar a este método para desbloquear el objeto de sección crítica.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta clase para bloquear y desbloquear objetos de forma más segura que con la [CComCriticalSection clase](../../atl/reference/ccomcriticalsection-class.md) o [CComAutoCriticalSection clase](../../atl/reference/ccomautocriticalsection-class.md).  
  
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
 Devuelve S_OK si el objeto se bloqueó correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto ya está bloqueado, se producirá un error de aserción en compilaciones de depuración.  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 Llamar a este método para desbloquear el objeto de sección crítica.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto ya está desbloqueado, se producirá un error de aserción en compilaciones de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection (clase)](../../atl/reference/ccomautocriticalsection-class.md)
