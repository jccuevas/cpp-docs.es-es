---
title: Clase ISupportErrorInfoImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e226f66d6ddd20181f083f723568acb1cc647c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364586"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl (clase)
Esta clase proporciona una implementación predeterminada de la [interfaz ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) y se puede usar cuando solo una única interfaz genera errores en un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>Parámetros  
 `piid`  
 Un puntero a lo IID de una interfaz que admite [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indica si la interfaz identificado por `riid` es compatible con la [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 El [interfaz ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) garantiza que se puede devolver información de error al cliente. Objetos que utilizan **IErrorInfo** debe implementar **ISupportErrorInfo**.  
  
 Clase `ISupportErrorInfoImpl` proporciona una implementación predeterminada de **ISupportErrorInfo** y se puede usar cuando solo una única interfaz genera errores en un objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 Indica si la interfaz identificado por `riid` es compatible con la [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) interfaz.  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a) en el SDK de Windows.  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 Llamar a este método para obtener el número de subprocesos en el grupo.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnNumThreads`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 Llamar a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `pdwMaxWait`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
 Llame a este método para establecer el número de subprocesos en el grupo.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
 Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
