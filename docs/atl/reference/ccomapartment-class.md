---
title: Clase CComApartment | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs: C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3fecd77e93c0c51a37d7363e6ec1472d157d6d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomapartment-class"></a>Clase CComApartment
Esta clase proporciona compatibilidad para administrar un apartamento de un módulo de archivo EXE agrupadas por subproceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComApartment
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|Marca la dirección inicial del subproceso.|  
|[CComApartment::GetLockCount](#getlockcount)|Devuelve el recuento de bloqueo actual del subproceso.|  
|[CComApartment::Lock](#lock)|Incrementa el recuento de bloqueo del subproceso.|  
|[CComApartment::Unlock](#unlock)|Reduce el recuento de bloqueo del subproceso.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contiene el identificador del subproceso.|  
|[CComApartment::m_hThread](#m_hthread)|Contiene el identificador del subproceso.|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contiene el recuento de bloqueo actual del subproceso.|  
  
## <a name="remarks"></a>Comentarios  
 `CComApartment`se utiliza por [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) para administrar un contenedor en un módulo de archivo EXE agrupadas por subproceso. `CComApartment`Proporciona métodos para aumentar y disminuir el bloqueo de contar con un subproceso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="apartment"></a>CComApartment::Apartment  
 Marca la dirección inicial del subproceso.  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es 0.  
  
### <a name="remarks"></a>Comentarios  
 Configura automáticamente durante la [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).  
  
##  <a name="ccomapartment"></a>CComApartment::CComApartment  
 El constructor.  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CComApartment` miembros de datos [m_nLockCnt](#m_nlockcnt) y [m_hThread](#m_hthread).  
  
##  <a name="getlockcount"></a>CComApartment::GetLockCount  
 Devuelve el recuento de bloqueo actual del subproceso.  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de bloqueos en el subproceso.  
  
##  <a name="lock"></a>CComApartment::Lock  
 Incrementa el recuento de bloqueo del subproceso.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o pruebas.  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el método [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 El recuento de bloqueos en el subproceso se usa para fines estadísticos.  
  
##  <a name="m_dwthreadid"></a>CComApartment::m_dwThreadID  
 Contiene el identificador del subproceso.  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>CComApartment::m_hThread  
 Contiene el identificador del subproceso.  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>CComApartment::m_nLockCnt  
 Contiene el recuento de bloqueo actual del subproceso.  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>CComApartment::Unlock  
 Reduce el recuento de bloqueo del subproceso.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o pruebas.  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el método [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 El recuento de bloqueos en el subproceso se usa para fines estadísticos.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
