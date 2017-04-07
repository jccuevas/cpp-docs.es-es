---
title: Interfaz de la interfaz IAxWinHostWindow | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- No header/ATL::IAxWinHostWindow
- No header/ATL::AttachControl
- No header/ATL::CreateControl
- No header/ATL::CreateControlEx
- No header/ATL::QueryControl
- No header/ATL::SetExternalDispatch
- No header/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e366e7e30e7b4080462fbc21c29b4ecdf0214ae
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinhostwindow-interface"></a>Interfaz IAxWinHostWindow (interfaz)
Esta interfaz proporciona métodos para manipular un control y su objeto de host.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
interface IAxWinHostWindow : IUnknown
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Asocia un control existente al objeto host.|  
|[CreateControl](#createcontrol)|Crea un control y lo adjunta al objeto host.|  
|[CreateControlEx](#createcontrolex)|Crea un control, se adjunta al objeto host y, opcionalmente, establece un controlador de eventos.|  
|[QueryControl](#querycontrol)|Devuelve un puntero de interfaz para el control hospedado.|  
|[SetExternalDispatch](#setexternaldispatch)|Establece la externa `IDispatch` interfaz.|  
|[SetExternalUIHandler](#setexternaluihandler)|Establece la externa `IDocHostUIHandlerDispatch` interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz expone objetos que hospeda los controles ActiveX de ATL. Llamar a los métodos de esta interfaz para crear o asociar un control para el objeto de host, para obtener una interfaz de un control hospedado, o para establecer la dispinterface externo o un controlador de interfaz de usuario para su uso cuando se hospedan en el explorador Web.  
  
## <a name="requirements"></a>Requisitos  
 La definición de esta interfaz está disponible como archivo IDL o C++, como se muestra a continuación.  
  
|Tipo de definición|Archivo|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow:: AttachControl  
 Asocia un control existente (e inicializado anteriormente) al objeto host mediante la ventana identificada por `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnkControl*  
 [in] Un puntero a la **IUnknown** interfaz del control que se va a vincular el objeto host.  
  
 `hWnd`  
 [in] Identificador de la ventana que se usará para hospedar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 Crea un control, lo inicializa y lo hospeda en la ventana identificada por `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpTricsData`  
 [in] Cadena que identifica el control que desee crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (con el prefijo **MSHTML:**).  
  
 `hWnd`  
 [in] Identificador de la ventana que se usará para hospedar.  
  
 `pStream`  
 [in] Puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto host exponer esta interfaz para que los mensajes se pueden reflejar en el control y otras características de contenedor funcionará se pueden crear subclases de esta ventana.  
  
 Llamar a este método equivale a llamar a [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, similar a [IAxWinHostWindow::CreateControl](#createcontrol).  
  
```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpTricsData`  
 [in] Cadena que identifica el control que desee crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (con el prefijo **MSHTML:**).  
  
 `hWnd`  
 [in] Identificador de la ventana que se usará para hospedar.  
  
 `pStream`  
 [in] Puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser **NULL**.  
  
 `ppUnk`  
 [out] La dirección de un puntero que recibirá la **IUnknown** interfaz del control creado. Puede ser **NULL**.  
  
 *riidAdvise*  
 [in] El identificador de la interfaz de la interfaz de salida en el objeto contenido. Puede ser **IID_NULL**.  
  
 *punkAdvise*  
 [in] Un puntero a la **IUnknown** interfaz del objeto receptor para conectarse al punto de conexión en el objeto contenido especificado por `iidSink`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de la `CreateControl` método `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.  
  
 Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `riid`  
 [in] El identificador de una interfaz en el control que se solicita.  
  
 `ppvObject`  
 [out] La dirección de un puntero que recibirá la interfaz especificada del control creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 Establece la interfaz dispinterface externa, que está disponible para los controles contenidos a través de la [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) método.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisp`  
 [in] Un puntero a un `IDispatch` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 Llame a esta función para establecer la externa [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) de interfaz para el `CAxWindow` objeto.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisp`  
 [in] Un puntero a un **IDocHostUIHandlerDispatch** interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza controles (como el control del explorador Web) que consultar el sitio del host de la `IDocHostUIHandlerDispatch` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetControl](http://msdn.microsoft.com/library/ad1f4f16-608d-4e96-8d30-04d4ca906a7b)










