---
title: Clase CAxWindow | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
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
ms.openlocfilehash: 202c68fa4044a7c7a6c47c52b8095c5e7227b56d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="caxwindow-class"></a>Clase CAxWindow
Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|Asocia un control ActiveX existente para la `CAxWindow` objeto.|  
|[CAxWindow](#caxwindow)|Construye un objeto `CAxWindow`.|  
|[CreateControl](#createcontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en el `CAxWindow` ventana.|  
|[CreateControlEx](#createcontrolex)|Crea un control ActiveX y recupera un puntero de interfaz (o punteros) del control.|  
|[GetWndClassName](#getwndclassname)|(Estático) Recupera el nombre de la clase predefinida de la `CAxWindow` objeto.|  
|[QueryControl](#querycontrol)|Recupera el **IUnknown** del control ActiveX hospedado.|  
|[QueryHost](#queryhost)|Recupera el **IUnknown** el puntero de la `CAxWindow` objeto.|  
|[SetExternalDispatch](#setexternaldispatch)|Establece la interfaz de envío externo utilizada por el `CAxWindow` objeto.|  
|[SetExternalUIHandler](#setexternaluihandler)|Establece la externa **IDocHostUIHandler** interfaz utilizada por el `CAxWindow` objeto.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](#operator_eq)|Asigna un **HWND** a un archivo **CAxWindow** objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX. Es el proceso de hospedaje proporcionada por " **AtlAxWin80"**, que se incluye en `CAxWindow`.  
  
 Clase `CAxWindow` se implementa como una especialización de la `CAxWindowT` clase. Esta especialización se declara como:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Si necesita cambiar la clase base, puede utilizar `CAxWindowT` y especifique la nueva clase base como un argumento de plantilla.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="attachcontrol"></a>CAxWindow::AttachControl  
 Crea un nuevo objeto de host si no está presente y se asocia el control especificado al host.  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControl`  
 [in] Un puntero a la **IUnknown** del control.  
  
 `ppUnkContainer`  
 [out] Un puntero a la **IUnknown** del host (el **AxWin** objeto).  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto de control que se va a asociar debe inicializarse correctamente antes de llamar a `AttachControl`.  
  
##  <a name="caxwindow"></a>CAxWindow::CAxWindow  
 Construye un `CAxWindow` objeto mediante un identificador de objeto de ventana existente.  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 Identificador de un objeto de ventana existente.  
  
##  <a name="createcontrol"></a>CAxWindow::CreateControl  
 Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.  
  
```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Un puntero a una cadena para crear el control. Debe tener el formato de una de las maneras siguientes:  
  
-   Un identificador de programa, como "MSCAL. Calendar.7 "  
  
-   CLSID, como "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\<corporal >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento de HTML para que se designa como una secuencia MSHTML. Sólo los ProgID y CLSID se admiten en las plataformas Windows Mobile. Windows CE incrustado plataformas, que no sea de Windows Mobile con compatibilidad para soporte técnico de IE CE todos los tipos incluidos ProgID, CLSID, URL, hacer referencia al documento activo y el fragmento de HTML.  
  
 `pStream`  
 [in] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 [out] La dirección de un puntero que recibirá la **IUnknown** del contenedor. Puede ser **NULL**.  
  
 `dwResID`  
 El identificador de recurso de un recurso HTML. El control WebBrowser y se cargan con el recurso especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si se utiliza la segunda versión de este método, se crea y se enlaza al recurso identificado por un control HTML `dwResID`.  
  
 Este método proporciona el mismo resultado que la llamada:  
  
 [!code-cpp[NVC_ATL_Windowing&#42;](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 Consulte [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) para crear, inicializar y hospedar un control ActiveX con licencia.  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControl`.  
  
##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx  
 Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.  
  
```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Un puntero a una cadena para crear el control. Debe tener el formato de una de las maneras siguientes:  
  
-   Un identificador de programa, como "MSCAL. Calendar.7 "  
  
-   CLSID, como "{8E27C92B-1264-101C-8A2F-040224009C02}"  
  
-   Una dirección URL como "http://www.microsoft.com"  
  
-   Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"  
  
-   Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\<corporal >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:" debe preceder el fragmento de HTML para que se designa como una secuencia MSHTML. Sólo los ProgID y CLSID se admiten en las plataformas Windows Mobile. Windows CE incrustado plataformas, que no sea de Windows Mobile con compatibilidad para soporte técnico de IE CE todos los tipos incluidos ProgID, CLSID, URL, hacer referencia al documento activo y el fragmento de HTML.  
  
 `pStream`  
 [in] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser **NULL**.  
  
 `ppUnkContainer`  
 [out] La dirección de un puntero que recibirá la **IUnknown** del contenedor. Puede ser **NULL**.  
  
 `ppUnkControl`  
 [out] La dirección de un puntero que recibirá la **IUnknown** del control. Puede ser **NULL**.  
  
 `iidSink`  
 [in] El identificador de la interfaz de la interfaz de salida en el objeto contenido. Puede ser **IID_NULL**.  
  
 *punkSink*  
 [in] Un puntero a la **IUnknown** interfaz del objeto receptor para conectarse al punto de conexión en el objeto contenido especificado por `iidSink`.  
  
 `dwResID`  
 [in] El identificador de recurso de un recurso HTML. El control WebBrowser y se cargan con el recurso especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Este método es similar a [CAxWindow::CreateControl](#createcontrol), pero a diferencia de ese método, `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.  
  
 Consulte [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) para crear, inicializar y hospedar un control ActiveX con licencia.  
  
### <a name="example"></a>Ejemplo  
 Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControlEx`.  
  
##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName  
 Recupera el nombre de la clase de ventana.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una cadena que contiene el nombre de la clase de ventana que puede hospedar controles ActiveX sin licencia.  
  
##  <a name="operator_eq"></a>CAxWindow::operator =  
 Asigna un `HWND` a un `CAxWindow` objeto.  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 Identificador de una ventana existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al objeto `CAxWindow` actual.  
  
##  <a name="querycontrol"></a>:: QueryControl  
 Recupera la interfaz especificada del control hospedado.  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] Especifica el IID de la interfaz del control.  
  
 `ppUnk`  
 [out] Puntero a la interfaz del control. En la versión de la plantilla de este método, no hay ninguna necesidad de un identificador de referencia siempre y cuando se pasa una interfaz con un UUID asociado.  
  
 `Q`  
 [in] La interfaz que se está consultando para.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="queryhost"></a>CAxWindow:: QueryHost  
 Devuelve la interfaz del host especificada.  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] Especifica el IID de la interfaz del control.  
  
 `ppUnk`  
 [out] Puntero a la interfaz del host. En la versión de la plantilla de este método, no hay ninguna necesidad de un identificador de referencia siempre y cuando se pasa una interfaz con un UUID asociado.  
  
 `Q`  
 [in] La interfaz que se está consultando para.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz del host permite el acceso a la funcionalidad subyacente del código de ventana que hospeda, implementada por **AxWin**.  
  
##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch  
 Establece la interfaz de envío externo para el `CAxWindow` objeto.  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisp`  
 [in] Un puntero a un `IDispatch` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler  
 Establece la externa [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) de interfaz para el `CAxWindow` objeto.  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUIHandler*  
 [in] Un puntero a un **IDocHostUIHandlerDispatch** interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Externo `IDocHostUIHandlerDispatch` interfaz se utiliza controles que consultar el sitio del host de la `IDocHostUIHandlerDispatch` interfaz. WebBrowser (control) es un control que lo haga.  
  
## <a name="see-also"></a>Vea también  
 [ATLCON (ejemplo)](../../visual-cpp-samples.md)   
 [CWindow (clase)](../../atl/reference/cwindow-class.md)   
 [Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Preguntas más frecuentes sobre la contención de controles](../../atl/atl-control-containment-faq.md)


