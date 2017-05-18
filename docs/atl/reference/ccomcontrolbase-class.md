---
title: Clase CComControlBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs:
- C++
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7ad253d42c916ec957ef1e6f5067027696103c79
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="ccomcontrolbase-class"></a>Clase CComControlBase
Esta clase proporciona métodos para crear y administrar los controles ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|Invalidar si su `m_nAppearance` propiedad estándar no es de tipo `short`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|El constructor.|  
|[CComControlBase:: ~ CComControlBase](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Comprueba que la `iVerb` parámetro utilizado por `IOleObjectImpl::DoVerb` una interfaz de usuario del control se activa ( `iVerb` es igual a `OLEIVERB_UIACTIVATE`), define la acción realizada cuando el usuario hace doble clic en el control ( `iVerb` es igual a `OLEIVERB_PRIMARY`), muestra el control ( `iVerb` es igual a `OLEIVERB_SHOW`), o activa el control ( `iVerb` es igual a **OLEIVERB_INPLACEACTIVATE**).|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Comprueba que la `iVerb` parámetro utilizado por `IOleObjectImpl::DoVerb` provoca la interfaz de usuario del control activar y vuelve **TRUE**.|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|Muestra las páginas de propiedades del control.|  
|[CComControlBase::FireViewChange](#fireviewchange)|Llamar a este método para indicar el contenedor para volver a dibujar el control, o para notificar a los receptores de notificación registrados que ha cambiado la vista del control.|  
|[CComControlBase:: GetAmbientAppearance](#getambientappearance)|Recupera **DISPID_AMBIENT_APPEARANCE**, la configuración para el control de presentación actual: 0 para plana y 1 para 3D.|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Recupera **DISPID_AMBIENT_AUTOCLIP**, una marca que indica si el contenedor admite recorte automática del área de presentación del control.|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Recupera **DISPID_AMBIENT_BACKCOLOR**, el color de fondo ambiente para todos los controles, definidos por el contenedor.|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Recupera **DISPID_AMBIENT_CHARSET**, el ambiente juego de caracteres para todos los controles, definidos por el contenedor.|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Recupera **DISPID_AMBIENT_CODEPAGE**, el ambiente juego de caracteres para todos los controles, definidos por el contenedor.|  
|[CComControlBase:: GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Recupera **DISPID_AMBIENT_DISPLAYASDEFAULT**, una marca que es **TRUE** si el contenedor marcó el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse a sí mismo con un marco más grueso.|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Recupera **DISPID_AMBIENT_DISPLAYNAME**, el nombre del contenedor se ha proporcionado para el control.|  
|[CComControlBase::GetAmbientFont](#getambientfont)|Recupera un puntero al contenedor del ambiente `IFont` interfaz.|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Recupera un puntero al contenedor del ambiente **IFontDisp** interfaz de envío.|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Recupera **DISPID_AMBIENT_FORECOLOR**, el color de primer plano ambiente para todos los controles, definidos por el contenedor.|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Recupera **DISPID_AMBIENT_LOCALEID**, el identificador del idioma utilizado por el contenedor.|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Recupera **DISPID_AMBIENT_MESSAGEREFLECT**, una marca que indica si el contenedor desea recibir mensajes de ventana (como `WM_DRAWITEM`) como eventos.|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Recupera **DISPID_AMBIENT_PALETTE**, que se usa para tener acceso al contenedor `HPALETTE`.|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Recupera la propiedad de contenedor especificada por `id`.|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Recupera **DISPID_AMBIENT_RIGHTTOLEFT**, la dirección en la que se muestra el contenido por el contenedor.|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Recupera **DISPID_AMBIENT_SCALEUNITS**, unidades de ambiente del contenedor (como pulgadas o centímetros) para etiquetar los muestra.|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Recupera **DISPID_AMBIENT_SHOWGRABHANDLES**, una marca que indica si el contenedor permite el control mostrar las asas de captación para sí mismo cuando está activo.|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Recupera **DISPID_AMBIENT_SHOWHATCHING**, una marca que indica si el contenedor permite el control aparezca con un patrón sombreado cuando la interfaz de usuario está activo.|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Recupera **DISPID_AMBIENT_SUPPORTSMNEMONICS**, una marca que indica si el contenedor admite teclas de acceso del teclado.|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Recupera **DISPID_AMBIENT_TEXTALIGN**, la alineación de texto preferida por el contenedor: 0 para la alineación general (números, texto a la derecha izquierda), 1 para la alineación a la izquierda, 2 para centrar y 3 para alineación a la derecha.|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Recupera **DISPID_AMBIENT_TOPTOBOTTOM**, la dirección en la que se muestra el contenido por el contenedor.|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Recupera **DISPID_AMBIENT_UIDEAD**, una marca que indica si el contenedor desea que el control para responder a las acciones de interfaz de usuario.|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Recupera **DISPID_AMBIENT_USERMODE**, una marca que indica si el contenedor está en modo de ejecución ( **TRUE**) o en modo de diseño ( **FALSE**).|  
|[CComControlBase::GetDirty](#getdirty)|Devuelve el valor del miembro de datos `m_bRequiresSave`.|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|Recupera el x e y valores del numerador y denominador del factor de zoom para activa un control de edición en contexto.|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Hace que el control para realizar la transición desde el estado inactivo para el estado que el verbo en `iVerb` indica.|  
|[CComControlBase::InternalGetSite](#internalgetsite)|Llamar a este método para consultar el sitio del control para un puntero a la interfaz identificada.|  
|[CComControlBase:: OnDraw](#ondraw)|Invalide este método para dibujar el control.|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|El valor predeterminado **OnDrawAdvanced** prepara un contexto de dispositivo normalizado para dibujar, a continuación, llama a la clase de control `OnDraw` método.|  
|[CComControlBase::OnKillFocus](#onkillfocus)|Comprueba que el control activo en contexto y tiene un sitio de control válidas, y después informa que el contenedor que el control ha perdido el foco.|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Comprueba que la interfaz de usuario está en modo de usuario, a continuación, activa el control.|  
|[CComControlBase::OnPaint](#onpaint)|Prepara el contenedor para dibujar, obtiene el área de cliente del control y, a continuación, llama a la clase de control `OnDraw` método.|  
|[CComControlBase::OnSetFocus](#onsetfocus)|Comprueba que el control está activo en contexto y tiene un sitio de control válidas e informa del contenedor del control ha obtenido el foco.|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Invalide este método para proporcionar su propio teclado controladores de aceleración.|  
|[CComControlBase::SendOnClose](#sendonclose)|Notifica a los receptores de todas las consultas registrados con el titular de la notificación que se ha cerrado el control.|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|Notifica a los receptores de todas las consultas registrados con el titular de la notificación que han cambiado los datos del control.|  
|[CComControlBase::SendOnRename](#sendonrename)|Notifica a los receptores de todas las consultas registrados con el titular de la notificación que el control tiene un moniker nuevo.|  
|[CComControlBase::SendOnSave](#sendonsave)|Notifica a los receptores de todas las consultas registrados con el titular de la notificación que se ha guardado el control.|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Notifica a que todos los receptores de consulta que ha cambiado la vista del control registrados.|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Establece o quita el foco del teclado a o desde el control.|  
|[CComControlBase::SetDirty](#setdirty)|Establece el miembro de datos `m_bRequiresSave` en el valor de `bDirty`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|Marca que indica que el control no puede ser cualquier otro tamaño.|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Marca que indica que `IDataObjectImpl::GetData` y `CComControlBase::GetZoomInfo` debe establecer el tamaño del control de `m_sizeNatural` en lugar de en `m_sizeExtent`.|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Marca que indica que `IDataObjectImpl::GetData` deben usar unidades HIMETRIC y no píxeles al dibujar.|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Marca que indica que el control está activo en contexto.|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Marca que indica el contenedor admite la **IOleInPlaceSiteEx** interfaz y OCX96 control de características, como los controles sin ventana y parpadeo.|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Marca que indica si el control se negocia con el contenedor sobre la compatibilidad con características de control de OCX96 (por ejemplo, los controles sin ventana y parpadeo), y si el control es con ventanas o sin ventana.|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Marca que indica el control que desea para volver a componer su presentación cuando el contenedor cambia el tamaño de presentación del control.|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Marca que indica que el control ha cambiado desde que se guardó por última vez.|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Marca que indica el control que desea cambiar el tamaño de su extensión natural (su tamaño físico sin ajuste de escala) cuando el contenedor cambia el tamaño de presentación del control.|  
|[CComControlBase::m_bUIActive](#m_buiactive)|Marca que indica la interfaz de usuario del control, como menús y barras de herramientas, está activo.|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Marca que indica que el control usa la región de ventana proporcionado por el contenedor.|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Marca que indica el control ha estado sin ventana, pero puede o no ser sin ventana ahora.|  
|[CComControlBase:: M_bwindowonly](#m_bwindowonly)|Marca que indica que el control debe ser división de particiones, incluso si el contenedor admite controles sin ventana.|  
|[CComControlBase::m_bWndLess](#m_bwndless)|Marca que indica que el control no tiene ventana.|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contiene una referencia al identificador de ventana asociada al control.|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Un recuento del número de veces que el contenedor ha inmovilizado eventos (rechazados Aceptar eventos) sin una reanudar intermedia de eventos (aceptación de eventos).|  
|[CComControlBase::m_rcPos](#m_rcpos)|La posición en píxeles del control, expresado en las coordenadas del contenedor.|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|La extensión del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros) para una pantalla concreta.|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|El tamaño físico del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros).|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un puntero directo a la conexión de consulta en el contenedor (el contenedor [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` objeto que permite recuperar y establecer las propiedades del contenedor a través de un `IDispatch` puntero.|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|Un puntero al sitio de cliente del control dentro del contenedor.|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Proporciona que un estándar de medios contener las conexiones entre los objetos de datos de consulta y receptores con notificación.|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Un puntero para el contenedor [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), o [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) puntero de interfaz.|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Proporciona una implementación estándar de una manera de contener conexiones de consulta.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para crear y administrar los controles ATL. [Clase CComControl](../../atl/reference/ccomcontrol-class.md) deriva de `CComControlBase`. Cuando se crea un control de Control estándar o DHTML mediante el Asistente para controles ATL, el asistente automáticamente derivará la clase de `CComControlBase`.  
  
 Para obtener más información acerca de cómo crear un control, vea el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="appearancetype"></a>CComControlBase::AppearanceType  
 Invalidar si su **m_nAppearance** propiedad estándar no es de tipo **corto**.  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>Comentarios  
 El Asistente para controles ATL agrega **m_nAppearance** propiedad de tipo corto estándar. Invalidar `AppearanceType` si usa un tipo de datos diferente.  
  
##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase  
 El constructor.  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>Parámetros  
 `h`  
 El identificador de la ventana asociada al control.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el tamaño del control unidades HIMETRIC de 5080 X 5080 (2 "X 2") e inicializa la `CComControlBase` valores de miembro de datos **NULL** o **FALSE**.  
  
##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase  
 Destructor.  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el control está con ventanas, `~CComControlBase` destruye mediante una llamada a [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682).  
  
##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 El GUID de la interfaz que se solicita.  
  
 `ppv`  
 Un puntero al puntero de interfaz identificado por `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Solo administra interfaces de la tabla de asignación COM.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM #15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate  
 Comprueba que la `iVerb` parámetro utilizado por `IOleObjectImpl::DoVerb` una interfaz de usuario del control se activa ( `iVerb` es igual a `OLEIVERB_UIACTIVATE`), define la acción realizada cuando el usuario hace doble clic en el control ( `iVerb` es igual a `OLEIVERB_PRIMARY`), muestra el control ( `iVerb` es igual a `OLEIVERB_SHOW`), o activa el control ( `iVerb` es igual a **OLEIVERB_INPLACEACTIVATE**).  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 Valor que indica la acción que debe realizar `DoVerb`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si `iVerb` es igual a `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, o **OLEIVERB_INPLACEACTIVATE**; en caso contrario, devuelve **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método para definir su propio verbo de activación.  
  
##  <a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate  
 Comprueba que la `iVerb` parámetro utilizado por `IOleObjectImpl::DoVerb` provoca la interfaz de usuario del control activar y vuelve **TRUE**.  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 Valor que indica la acción que debe realizar `DoVerb`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si `iVerb` es igual a `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, o **OLEIVERB_INPLACEACTIVATE**. En caso contrario, el método devuelve **FALSE**.  
  
##  <a name="doverbproperties"></a>CComControlBase::DoVerbProperties  
 Muestra las páginas de propiedades del control.  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 Reservado.  
  
 *hwndParent*  
 Identificador de la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM #19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM Nº 20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>CComControlBase::FireViewChange  
 Llamar a este método para indicar el contenedor para volver a dibujar el control, o para notificar a los receptores de notificación registrados que ha cambiado la vista del control.  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si el control está activo (el miembro de datos de la clase de control [CComControlBase::m_bInPlaceActive](#m_binplaceactive) es **TRUE**), notifica al contenedor que desea volver a dibujar todo el control. Si el control está inactivo, el control del registrado notifica a receptores con notificación (a través del miembro de datos de la clase de control [CComControlBase::m_spAdviseSink](#m_spadvisesink)) que ha cambiado la vista del control.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM #21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>CComControlBase:: GetAmbientAppearance  
 Recupera **DISPID_AMBIENT_APPEARANCE**, la configuración para el control de presentación actual: 0 para plana y 1 para 3D.  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>Parámetros  
 `nAppearance`  
 La propiedad **DISPID_AMBIENT_APPEARANCE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM #22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip  
 Recupera **DISPID_AMBIENT_AUTOCLIP**, una marca que indica si el contenedor admite recorte automática del área de presentación del control.  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAutoClip*  
 La propiedad **DISPID_AMBIENT_AUTOCLIP**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor  
 Recupera **DISPID_AMBIENT_BACKCOLOR**, el color de fondo ambiente para todos los controles, definidos por el contenedor.  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *Color de fondo*  
 La propiedad **DISPID_AMBIENT_BACKCOLOR**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet  
 Recupera **DISPID_AMBIENT_CHARSET**, el ambiente juego de caracteres para todos los controles, definidos por el contenedor.  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>Parámetros  
 *bstrCharSet*  
 La propiedad **DISPID_AMBIENT_CHARSET**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage  
 Recupera **DISPID_AMBIENT_CODEPAGE**, la página de códigos ambiente para todos los controles, definidos por el contenedor.  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>Parámetros  
 *ulCodePage*  
 La propiedad **DISPID_AMBIENT_CODEPAGE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="getambientdisplayasdefault"></a>CComControlBase:: GetAmbientDisplayAsDefault  
 Recupera **DISPID_AMBIENT_DISPLAYASDEFAULT**, una marca que es **TRUE** si el contenedor marcó el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse a sí mismo con un marco más grueso.  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDisplayAsDefault`  
 La propiedad **DISPID_AMBIENT_DISPLAYASDEFAULT**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName  
 Recupera **DISPID_AMBIENT_DISPLAYNAME**, el nombre del contenedor se ha proporcionado para el control.  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>Parámetros  
 *bstrDisplayName*  
 La propiedad **DISPID_AMBIENT_DISPLAYNAME**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont  
 Recupera un puntero al contenedor del ambiente `IFont` interfaz.  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppFont`  
 Un puntero al contenedor del ambiente [IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673) interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la propiedad es **NULL**, el puntero es **NULL**. Si el puntero no es **NULL**, el llamador debe liberar el puntero.  
  
##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp  
 Recupera un puntero al contenedor del ambiente **IFontDisp** interfaz de envío.  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppFont`  
 Un puntero al contenedor del ambiente [IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695) interfaz de envío.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si la propiedad es **NULL**, el puntero es **NULL**. Si el puntero no es **NULL**, el llamador debe liberar el puntero.  
  
##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor  
 Recupera **DISPID_AMBIENT_FORECOLOR**, el color de primer plano ambiente para todos los controles, definidos por el contenedor.  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *Color de primer plano*  
 La propiedad **DISPID_AMBIENT_FORECOLOR**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID  
 Recupera **DISPID_AMBIENT_LOCALEID**, el identificador del idioma utilizado por el contenedor.  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>Parámetros  
 `lcid`  
 La propiedad **DISPID_AMBIENT_LOCALEID**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El control puede utilizar este identificador para adaptar la interfaz de usuario en diferentes idiomas.  
  
##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect  
 Recupera **DISPID_AMBIENT_MESSAGEREFLECT**, una marca que indica si el contenedor desea recibir mensajes de ventana (como `WM_DRAWITEM`) como eventos.  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>Parámetros  
 `bMessageReflect`  
 La propiedad **DISPID_AMBIENT_MESSAGEREFLECT**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette  
 Recupera **DISPID_AMBIENT_PALETTE**, que se usa para tener acceso al contenedor `HPALETTE`.  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `hPalette`  
 La propiedad **DISPID_AMBIENT_PALETTE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty  
 Recupera la propiedad de contenedor especificada por `dispid`.  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Identificador de la propiedad de contenedor que se va a recuperar.  
  
 `var`  
 Variable para recibir la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 ATL ha proporcionado un conjunto de funciones auxiliares para recuperar determinadas propiedades, por ejemplo, [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Si no hay disponible ningún método adecuado, utilice `GetAmbientProperty`.  
  
##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft  
 Recupera **DISPID_AMBIENT_RIGHTTOLEFT**, la dirección en la que se muestra el contenido por el contenedor.  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>Parámetros  
 *bRightToLeft*  
 La propiedad **DISPID_AMBIENT_RIGHTTOLEFT**. Establecido en **TRUE** si se muestra el contenido de derecha a izquierda, **FALSE** si se muestra de izquierda a derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits  
 Recupera **DISPID_AMBIENT_SCALEUNITS**, unidades de ambiente del contenedor (como pulgadas o centímetros) para etiquetar los muestra.  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>Parámetros  
 *bstrScaleUnits*  
 La propiedad **DISPID_AMBIENT_SCALEUNITS**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles  
 Recupera **DISPID_AMBIENT_SHOWGRABHANDLES**, una marca que indica si el contenedor permite el control mostrar las asas de captación para sí mismo cuando está activo.  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>Parámetros  
 *bShowGrabHandles*  
 La propiedad **DISPID_AMBIENT_SHOWGRABHANDLES**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching  
 Recupera **DISPID_AMBIENT_SHOWHATCHING**, una marca que indica si el contenedor permite el control aparezca con un patrón sombreado cuando está activa la interfaz de usuario del control.  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>Parámetros  
 *bShowHatching*  
 La propiedad **DISPID_AMBIENT_SHOWHATCHING**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics  
 Recupera **DISPID_AMBIENT_SUPPORTSMNEMONICS**, una marca que indica si el contenedor admite teclas de acceso del teclado.  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>Parámetros  
 *bSupportsMnemonics*  
 La propiedad **DISPID_AMBIENT_SUPPORTSMNEMONICS**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign  
 Recupera **DISPID_AMBIENT_TEXTALIGN**, la alineación de texto preferida por el contenedor: 0 para la alineación general (números, texto a la derecha izquierda), 1 para la alineación a la izquierda, 2 para centrar y 3 para alineación a la derecha.  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>Parámetros  
 *nTextAlign*  
 La propiedad **DISPID_AMBIENT_TEXTALIGN**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom  
 Recupera **DISPID_AMBIENT_TOPTOBOTTOM**, la dirección en la que se muestra el contenido por el contenedor.  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>Parámetros  
 *bTopToBottom*  
 La propiedad **DISPID_AMBIENT_TOPTOBOTTOM**. Establecido en **TRUE** si el texto que aparece arriba a abajo, **FALSE** si se muestra abajo a arriba.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead  
 Recupera **DISPID_AMBIENT_UIDEAD**, una marca que indica si el contenedor desea que el control para responder a las acciones de interfaz de usuario.  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>Parámetros  
 *bUIDead*  
 La propiedad **DISPID_AMBIENT_UIDEAD**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si **TRUE**, el control no debería responder. Esta marca se aplica independientemente de la **DISPID_AMBIENT_USERMODE** marca. Vea [CComControlBase::GetAmbientUserMode](#getambientusermode).  
  
##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode  
 Recupera **DISPID_AMBIENT_USERMODE**, una marca que indica si el contenedor está en modo de ejecución ( **TRUE**) o en modo de diseño ( **FALSE**).  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `bUserMode`  
 La propiedad **DISPID_AMBIENT_USERMODE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
##  <a name="getdirty"></a>CComControlBase::GetDirty  
 Devuelve el valor del miembro de datos `m_bRequiresSave`.  
  
```
BOOL GetDirty();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del miembro de datos [m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Comentarios  
 Este valor se establece mediante [CComControlBase::SetDirty](#setdirty).  
  
##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo  
 Recupera el x e y valores del numerador y denominador del factor de zoom para activa un control de edición en contexto.  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parámetros  
 `di`  
 La estructura que contendrá el factor de zoom numerador y denominador. Para obtener más información, consulte [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).  
  
### <a name="remarks"></a>Comentarios  
 El factor de zoom es la proporción de tamaño natural del control a su tamaño actual.  
  
##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate  
 Hace que el control para realizar la transición desde el estado inactivo para el estado que el verbo en `iVerb` indica.  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 Valor que indica la acción que debe realizar [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).  
  
 *prcPosRect*  
 Puntero a la posición del control en contexto.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Antes de la activación, este método comprueba que el control tiene un sitio de cliente, comprueba la cantidad del control está visible y obtiene la ubicación del control en la ventana primaria. Después de activa el control, este método activa la interfaz de usuario del control e indica al contenedor para que el control sea visible.  
  
 Este método también recupera un `IOleInPlaceSite`, **IOleInPlaceSiteEx**, o **IOleInPlaceSiteWindowless** puntero de interfaz para el control y lo almacena en el miembro de datos de la clase de control [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Los miembros de datos de la clase de control [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless), y [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) están establecidos en true según corresponda.  
  
##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite  
 Llamar a este método para consultar el sitio del control para un puntero a la interfaz identificada.  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>Parámetros  
 `riid`  
 El IID del puntero de interfaz que se debe devolver en `ppUnkSite`.  
  
 `ppUnkSite`  
 Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en `riid`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si el sitio admite la interfaz solicitada en `riid`, se devuelve el puntero por medio de `ppUnkSite`. En caso contrario, `ppUnkSite` se establece en NULL.  
  
##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize  
 Marca que indica que el control no puede ser cualquier otro tamaño.  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta marca está activada de forma `IOleObjectImpl::SetExtent` y, si **TRUE**, hace que la función devuelva **E_FAIL**.  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 Si agrega el **tamaño automático** opción el [propiedades estándar](../../atl/reference/stock-properties-atl-control-wizard.md) ficha del Asistente de Control ATL, el asistente crea este miembro de datos en la clase del control, crea put y automáticamente para la propiedad y es compatible con los métodos get [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) para notificar automáticamente el contenedor cuando cambia la propiedad.  
  
##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural  
 Marca que indica que `IDataObjectImpl::GetData` y `CComControlBase::GetZoomInfo` debe establecer el tamaño del control de `m_sizeNatural` en lugar de en `m_sizeExtent`.  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric  
 Marca que indica que `IDataObjectImpl::GetData` deben usar unidades HIMETRIC y no píxeles al dibujar.  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>Comentarios  
 Cada unidad lógica de HIMETRIC es de 0,01 milímetros.  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive  
 Marca que indica que el control está activo en contexto.  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>Comentarios  
 Esto significa que el control está visible y su ventana, si existe, está visible, pero es podrán que sus menús y barras de herramientas no esté activas. El `m_bUIActive` marca indica la interfaz de usuario del control, como menús, también está activa.  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx  
 Marca que indica el contenedor admite la **IOleInPlaceSiteEx** interfaz y OCX96 control de características, como los controles sin ventana y parpadeo.  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 El miembro de datos `m_spInPlaceSite` apunta a un [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), o [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interfaz, dependiendo del valor de la `m_bWndLess` y `m_bInPlaceSiteEx` marcas. (El miembro de datos `m_bNegotiatedWnd` debe ser **TRUE** para el `m_spInPlaceSite` puntero sea válido.)  
  
 Si `m_bWndLess` es **FALSE** y `m_bInPlaceSiteEx` es **TRUE**, `m_spInPlaceSite` es un **IOleInPlaceSiteEx** puntero de interfaz. Vea [m_spInPlaceSite](#m_spinplacesite) para una tabla que muestra la relación entre estos tres miembros de datos.  
  
##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd  
 Marca que indica si el control se negocia con el contenedor sobre la compatibilidad con características de control de OCX96 (por ejemplo, los controles sin ventana y parpadeo), y si el control es con ventanas o sin ventana.  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 El `m_bNegotiatedWnd` marca debe ser **TRUE** para el `m_spInPlaceSite` puntero sea válida.  
  
##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize  
 Marca que indica el control que desea para volver a componer su presentación cuando el contenedor cambia el tamaño de presentación del control.  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 Esta marca está activada de forma [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) y, si **TRUE**, `SetExtent` notifica al contenedor de ver los cambios. Si se establece esta marca, el **OLEMISC_RECOMPOSEONRESIZE** de bits en el [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) también debe establecerse la enumeración.  
  
##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave  
 Marca que indica que el control ha cambiado desde que se guardó por última vez.  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>Comentarios  
 El valor de `m_bRequiresSave` se puede establecer con [CComControlBase::SetDirty](#setdirty) y se recuperan con [CComControlBase::GetDirty](#getdirty).  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural  
 Marca que indica el control que desea cambiar el tamaño de su extensión natural (su tamaño físico sin ajuste de escala) cuando el contenedor cambia el tamaño de presentación del control.  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta marca está activada de forma `IOleObjectImpl::SetExtent` y, si **TRUE**, pasará el tamaño `SetExtent` se asigna a `m_sizeNatural`.  
  
 El tamaño que se pasa en `SetExtent` siempre se asigna a `m_sizeExtent`, independientemente del valor de `m_bResizeNatural`.  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive  
 Marca que indica la interfaz de usuario del control, como menús y barras de herramientas, está activo.  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_bInPlaceActive` marca indica que el control está activo, pero no que la interfaz de usuario está activa.  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn  
 Marca que indica que el control usa la región de ventana proporcionado por el contenedor.  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless  
 Marca que indica el control ha estado sin ventana, pero puede o no ser sin ventana ahora.  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_bwindowonly"></a>CComControlBase:: M_bwindowonly  
 Marca que indica que el control debe ser división de particiones, incluso si el contenedor admite controles sin ventana.  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess  
 Marca que indica que el control no tiene ventana.  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 El miembro de datos `m_spInPlaceSite` apunta a un [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), o [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) interfaz, dependiendo del valor de la `m_bWndLess` y [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) marcas. (El miembro de datos [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) debe ser **TRUE** para el [CComControlBase::m_spInPlaceSite](#m_spinplacesite) puntero sea válido.)  
  
 Si `m_bWndLess` es **TRUE**, `m_spInPlaceSite` es un **IOleInPlaceSiteWindowless** puntero de interfaz. Vea [CComControlBase::m_spInPlaceSite](#m_spinplacesite) para una tabla que muestra la relación entre estos miembros de datos completa.  
  
##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD  
 Contiene una referencia al identificador de ventana asociada al control.  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents  
 Un recuento del número de veces que el contenedor ha inmovilizado eventos (rechazados Aceptar eventos) sin una reanudar intermedia de eventos (aceptación de eventos).  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_rcpos"></a>CComControlBase::m_rcPos  
 La posición en píxeles del control, expresado en las coordenadas del contenedor.  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent  
 La extensión del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros) para una pantalla concreta.  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 Este tamaño se escala por la pantalla. El tamaño del control físico se especifica en el `m_sizeNatural` miembro de datos y se ha corregido.  
  
 Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural  
 El tamaño físico del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros).  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 Este tamaño es fijo, mientras el tamaño en `m_sizeExtent` se escala por la pantalla.  
  
 Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink  
 Un puntero directo a la conexión de consulta en el contenedor (el contenedor [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch  
 A `CComDispatchDriver` objeto que permite recuperar y establecer las propiedades de un objeto a través de un `IDispatch` puntero.  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite  
 Un puntero al sitio de cliente del control dentro del contenedor.  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder  
 Proporciona que un estándar de medios contener las conexiones entre los objetos de datos de consulta y receptores con notificación.  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 Un objeto de datos es un control que pueden transferir datos y que implementa [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), cuyos métodos especifican el medio de formato y la transferencia de los datos.  
  
 La interfaz `m_spDataAdviseHolder` implementa la [IDataObject:: DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) y [IDataObject:: DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) métodos para establecer y eliminar conexiones de consulta para el contenedor. El contenedor del control debe implementar un receptor con notificación ya que admite la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfaz.  
  
##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite  
 Un puntero para el contenedor [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), o [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) puntero de interfaz.  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 El `m_spInPlaceSite` puntero es válido únicamente si el [m_bNegotiatedWnd](#m_bnegotiatedwnd) marca es **TRUE**.  
  
 La tabla siguiente muestra cómo el `m_spInPlaceSite` depende de tipo de puntero el [m_bWndLess](#m_bwndless) y [m_bInPlaceSiteEx](#m_binplacesiteex) indicadores de miembros de datos:  
  
|Tipo de m_spInPlaceSite|m_bWndLess valor|m_bInPlaceSiteEx valor|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**ES TRUE**|**TRUE** o **FALSE**|  
|**IOleInPlaceSiteEx**|**FALSE**|**ES TRUE**|  
|`IOleInPlaceSite`|**FALSE**|**FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder  
 Proporciona una implementación estándar de una manera de contener conexiones de consulta.  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Para utilizar a este miembro de datos dentro de la clase de control, debe declararlo como un miembro de datos en la clase del control. La clase del control no heredará a este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.  
  
 La interfaz `m_spOleAdviseHolder` implementa la [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) y [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) métodos para establecer y eliminar conexiones de consulta para el contenedor. El contenedor del control debe implementar un receptor con notificación ya que admite la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfaz.  
  
##  <a name="ondraw"></a>CComControlBase:: OnDraw  
 Invalide este método para dibujar el control.  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parámetros  
 `di`  
 Una referencia a la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) estructura que contiene información de dibujo, como el aspecto de dibujo, los límites del control, y si se optimiza el dibujo o no.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado `OnDraw` elimina o restaura el contexto de dispositivo o no hace nada, dependiendo de los indicadores establecidos [CComControlBase::OnDrawAdvanced](#ondrawadvanced).  
  
 Un `OnDraw` método se agrega automáticamente a la clase del control cuando se crea el control con el Asistente para controles ATL. Valor predeterminado del asistente `OnDraw` dibuja un rectángulo con la etiqueta "ATL 8.0".  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CComControlBase:: GetAmbientAppearance](#getambientappearance).  
  
##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced  
 El valor predeterminado `OnDrawAdvanced` prepara un contexto de dispositivo normalizado para dibujar, a continuación, llama a la clase de control `OnDraw` método.  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parámetros  
 `di`  
 Una referencia a la [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) estructura que contiene información de dibujo, como el aspecto de dibujo, los límites del control, y si se optimiza el dibujo o no.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea aceptar el contexto de dispositivo que se pasa por el contenedor sin normalizar se.  
  
 Vea [CComControlBase:: OnDraw](#ondraw) para obtener más detalles.  
  
##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus  
 Comprueba que el control activo en contexto y tiene un sitio de control válidas, y después informa que el contenedor que el control ha perdido el foco.  
  
```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMsg`  
 Reservado.  
  
 `wParam`  
 Reservado.  
  
 `lParam`  
 Reservado.  
  
 `bHandled`  
 Marca que indica si el mensaje de ventana se controló correctamente. De manera predeterminada, es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate  
 Comprueba que la interfaz de usuario está en modo de usuario, a continuación, activa el control.  
  
```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMsg`  
 Reservado.  
  
 `wParam`  
 Reservado.  
  
 `lParam`  
 Reservado.  
  
 `bHandled`  
 Marca que indica si el mensaje de ventana se controló correctamente. De manera predeterminada, es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
##  <a name="onpaint"></a>CComControlBase::OnPaint  
 Prepara el contenedor para dibujar, obtiene el área de cliente del control y, a continuación, llama a la clase de control `OnDrawAdvanced` método.  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMsg`  
 Reservado.  
  
 `wParam`  
 HDC existente.  
  
 `lParam`  
 Reservado.  
  
 `lResult`  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve cero.  
  
### <a name="remarks"></a>Comentarios  
 Si `wParam` no es NULL, `OnPaint` supone contiene un HDC válido y utiliza en lugar del [CComControlBase::m_hWndCD](#m_hwndcd).  
  
##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus  
 Comprueba que el control está activo en contexto y tiene un sitio de control válidas e informa del contenedor del control ha obtenido el foco.  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMsg`  
 Reservado.  
  
 `wParam`  
 Reservado.  
  
 `lParam`  
 Reservado.  
  
 `bHandled`  
 Marca que indica si el mensaje de ventana se controló correctamente. De manera predeterminada, es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
 Envía una notificación al contenedor que el control ha recibido el foco.  
  
##  <a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator  
 Invalide este método para proporcionar su propio teclado controladores de aceleración.  
  
```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Reservado.  
  
 *hRet*  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 De forma predeterminada, devuelve **FALSE**.  
  
##  <a name="sendonclose"></a>CComControlBase::SendOnClose  
 Notifica a los receptores de todas las consultas registrados con el titular de la notificación que se ha cerrado el control.  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Envía una notificación de que el control ha cerrado sus receptores de consultas.  
  
##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange  
 Notifica a los receptores de todas las consultas registrados con el titular de la notificación que han cambiado los datos del control.  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *ADVF*  
 Aconseje marcas que especifican cómo la llamada a [IAdviseSink:: OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283) se realiza. Los valores son de la [ADVF](http://msdn.microsoft.com/library/windows/desktop/ms693742) enumeración.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="sendonrename"></a>CComControlBase::SendOnRename  
 Notifica a los receptores de todas las consultas registrados con el titular de la notificación que el control tiene un moniker nuevo.  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>Parámetros  
 *PMK*  
 Puntero al nuevo moniker del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Envía una notificación de que ha cambiado el moniker para el control.  
  
##  <a name="sendonsave"></a>CComControlBase::SendOnSave  
 Notifica a los receptores de todas las consultas registrados con el titular de la notificación que se ha guardado el control.  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Envía una notificación de que el control seguiría sus datos.  
  
##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange  
 Notifica a que todos los receptores de consulta que ha cambiado la vista del control registrados.  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwAspect`  
 El aspecto o la vista del control.  
  
 *lIndex*  
 La parte de la vista que ha cambiado. Solo -1 es válido.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `SendOnViewChange`llamadas [IAdviseSink:: OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337). El único valor de *lindex* admite actualmente es -1, lo que indica que la vista completa de interés.  
  
##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus  
 Establece o quita el foco del teclado a o desde el control.  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>Parámetros  
 *bGrab*  
 Si **TRUE**, Establece el foco del teclado al control que realiza la llamada. Si **FALSE**, quita el foco del teclado del control que llama, siempre que haya el foco.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si el control recibe correctamente el foco; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para un control con ventanas, la función de API de Windows [SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312) se llama. Para un control sin ventana, [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745) se llama. Mediante esta llamada, un control sin ventana Obtiene el foco del teclado y puede responder a mensajes de ventana.  
  
##  <a name="setdirty"></a>CComControlBase::SetDirty  
 Establece el miembro de datos `m_bRequiresSave` en el valor de `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDirty`  
 Valor del miembro de datos [CComControlBase::m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Comentarios  
 **SetDirty(TRUE)** se debe llamar para marcar que el control ha cambiado desde que se guardó por última vez. El valor de `m_bRequiresSave` se recupera con [CComControlBase::GetDirty](#getdirty).  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

