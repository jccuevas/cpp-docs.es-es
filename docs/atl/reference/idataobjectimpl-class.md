---
title: Clase IDataObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: afd5fe7cf9bbac582e59ed46dc33e99de5fc2876
ms.lasthandoff: 02/24/2017

---
# <a name="idataobjectimpl-class"></a>Clase IDataObjectImpl
Esta clase proporciona métodos para admitir la transferencia de datos uniforme y administración de conexiones.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IDataObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|Establece una conexión entre el objeto de datos y un receptor con notificación. Esto permite al receptor con notificación recibir notificaciones de cambios en el objeto.|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|Finaliza una conexión establecida previamente a través de `DAdvise`.|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Crea un enumerador para recorrer en iteración la **FORMATETC** estructuras que admite el objeto de datos. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|Envía una notificación de cambio a cada receptor de notificaciones.|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Recupera un lógicamente equivalente **FORMATETC** estructura a uno que es más complejo. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::GetData](#getdata)|Transfiere los datos del objeto de datos al cliente. Describe los datos en un **FORMATETC** estructurar y se transfieren a través de un **STGMEDIUM** estructura.|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|Similar a `GetData`, excepto en que el cliente debe asignar el **STGMEDIUM** estructura. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|Determina si el objeto de datos admite una determinada **FORMATETC** estructura de transferencia de datos. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::SetData](#setdata)|Transfiere los datos desde el cliente al objeto de datos. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 El [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) interfaz proporciona métodos para admitir la transferencia de datos uniforme. `IDataObject`utiliza las estructuras de formato estándar [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) y [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) para recuperar y almacenar datos.  
  
 `IDataObject`También administra las conexiones para informar a los receptores para controlar las notificaciones de cambio de datos. El cliente puede recibir notificaciones de cambio de datos del objeto de datos, el cliente debe implementar la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfaz en un objeto denominado un receptor con notificación. Cuando el cliente llama a continuación, **IDataObject:: DAdvise**, se establece una conexión entre el objeto de datos y el receptor de notificaciones.  
  
 Clase `IDataObjectImpl` proporciona una implementación predeterminada de `IDataObject` e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="dadvise"></a>IDataObjectImpl::DAdvise  
 Establece una conexión entre el objeto de datos y un receptor con notificación.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Esto permite al receptor con notificación recibir notificaciones de cambios en el objeto.  
  
 Para finalizar la conexión, llame a [DUnadvise](#dunadvise).  
  
 Consulte [IDataObject:: DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="dunadvise"></a>IDataObjectImpl::DUnadvise  
 Finaliza una conexión establecida previamente a través de [DAdvise](#dadvise).  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise  
 Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc  
 Crea un enumerador para recorrer en iteración la **FORMATETC** estructuras que admite el objeto de datos.  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
##  <a name="firedatachange"></a>IDataObjectImpl::FireDataChange  
 Envía una notificación de cambio a cada receptor de notificaciones que se está administrando.  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc  
 Recupera un lógicamente equivalente **FORMATETC** estructura a uno que es más complejo.  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getdata"></a>IDataObjectImpl::GetData  
 Transfiere los datos del objeto de datos al cliente.  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>Comentarios  
 El *pformatetcIn* parámetro debe especificar un tipo de medio de almacenamiento de **TYMED_MFPICT**.  
  
 Consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getdatahere"></a>IDataObjectImpl::GetDataHere  
 Similar a `GetData`, excepto en que el cliente debe asignar el **STGMEDIUM** estructura.  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: GetDataHere](http://msdn.microsoft.com/library/windows/desktop/ms687266) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="querygetdata"></a>IDataObjectImpl::QueryGetData  
 Determina si el objeto de datos admite una determinada **FORMATETC** estructura de transferencia de datos.  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setdata"></a>IDataObjectImpl::SetData  
 Transfiere los datos desde el cliente al objeto de datos.  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDataObject:: SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

