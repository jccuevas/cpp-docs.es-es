---
title: "CComControlBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComControlBase"
  - "ATL.CComControlBase"
  - "ATL::CComControlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComControlBase class"
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComControlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y administrar controles ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class ATL_NO_VTABLE CComControlBase  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](../Topic/CComControlBase::AppearanceType.md)|Reemplace si la propiedad de la acción de `m_nAppearance` no es de `short`escrito.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](../Topic/CComControlBase::CComControlBase.md)|el constructor.|  
|[CComControlBase::~CComControlBase](../Topic/CComControlBase::~CComControlBase.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](../Topic/CComControlBase::ControlQueryInterface.md)|recupera un puntero a la interfaz solicitada.|  
|[CComControlBase::DoesVerbActivate](../Topic/CComControlBase::DoesVerbActivate.md)|Comprueba que el parámetro de `iVerb` utilizado por `IOleObjectImpl::DoVerb` cualquiera genera la interfaz de usuario del control \(`iVerb` es igual a `OLEIVERB_UIACTIVATE`\), defina la acción realizada cuando el usuario hace doble clic en el control \(`iVerb` es igual a `OLEIVERB_PRIMARY`\), muestran el control \(`iVerb` es igual a `OLEIVERB_SHOW`\), o provocan el control \(`iVerb` es igual a **OLEIVERB\_INPLACEACTIVATE**\).|  
|[CComControlBase::DoesVerbUIActivate](../Topic/CComControlBase::DoesVerbUIActivate.md)|Comprueba que el parámetro de `iVerb` utilizado por `IOleObjectImpl::DoVerb` hace que la interfaz de usuario del control para generar y devuelven **TRUE**.|  
|[CComControlBase::DoVerbProperties](../Topic/CComControlBase::DoVerbProperties.md)|Muestra las páginas de propiedades del control.|  
|[CComControlBase::FireViewChange](../Topic/CComControlBase::FireViewChange.md)|Llame a este método para indicar al contenedor que actualizar el control, o notificar a registrado indican los receptores que la vista de control ha cambiado.|  
|[CComControlBase::GetAmbientAppearance](../Topic/CComControlBase::GetAmbientAppearance.md)|Recupera **DISPID\_AMBIENT\_APPEARANCE**, el valor actual de apariencia del control: 0 para el plano y 1 para 3D.|  
|[CComControlBase::GetAmbientAutoClip](../Topic/CComControlBase::GetAmbientAutoClip.md)|Recupera **DISPID\_AMBIENT\_AUTOCLIP**, una marca que indica si el contenedor admite el recorte automático del área de presentación del control.|  
|[CComControlBase::GetAmbientBackColor](../Topic/CComControlBase::GetAmbientBackColor.md)|Recupera **DISPID\_AMBIENT\_BACKCOLOR**, el color de fondo ambiente para todos los controles, definido por el contenedor.|  
|[CComControlBase::GetAmbientCharSet](../Topic/CComControlBase::GetAmbientCharSet.md)|Recupera **DISPID\_AMBIENT\_CHARSET**, el juego de caracteres ambiente para todos los controles, definido por el contenedor.|  
|[CComControlBase::GetAmbientCodePage](../Topic/CComControlBase::GetAmbientCodePage.md)|Recupera **DISPID\_AMBIENT\_CODEPAGE**, el juego de caracteres ambiente para todos los controles, definido por el contenedor.|  
|[CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md)|Recupera **DISPID\_AMBIENT\_DISPLAYASDEFAULT**, un marcador que se **TRUE** si el contenedor ha marcado el control en este sitio para ser un botón predeterminado y, por consiguiente un control button debe dibujarse a sí mismo con un cuadro más general.|  
|[CComControlBase::GetAmbientDisplayName](../Topic/CComControlBase::GetAmbientDisplayName.md)|Recupera **DISPID\_AMBIENT\_DISPLAYNAME**, el nombre que el contenedor ha proporcionado al control.|  
|[CComControlBase::GetAmbientFont](../Topic/CComControlBase::GetAmbientFont.md)|Recupera un puntero a la interfaz ambiente de `IFont` del contenedor.|  
|[CComControlBase::GetAmbientFontDisp](../Topic/CComControlBase::GetAmbientFontDisp.md)|Recupera un puntero a la interfaz de envío ambiente de **IFontDisp** del contenedor.|  
|[CComControlBase::GetAmbientForeColor](../Topic/CComControlBase::GetAmbientForeColor.md)|Recupera **DISPID\_AMBIENT\_FORECOLOR**, el color de primer plano ambiente para todos los controles, definido por el contenedor.|  
|[CComControlBase::GetAmbientLocaleID](../Topic/CComControlBase::GetAmbientLocaleID.md)|Recupera **DISPID\_AMBIENT\_LOCALEID**, el identificador del lenguaje utilizado por el contenedor.|  
|[CComControlBase::GetAmbientMessageReflect](../Topic/CComControlBase::GetAmbientMessageReflect.md)|Recupera **DISPID\_AMBIENT\_MESSAGEREFLECT**, una marca que indica si el contenedor desea recibir mensajes de la ventana \(como `WM_DRAWITEM`\) como eventos.|  
|[CComControlBase::GetAmbientPalette](../Topic/CComControlBase::GetAmbientPalette.md)|Recupera **DISPID\_AMBIENT\_PALETTE**, se utiliza para tener acceso a `HPALETTE`del contenedor.|  
|[CComControlBase::GetAmbientProperty](../Topic/CComControlBase::GetAmbientProperty.md)|Recupera la propiedad container especificada por `id`.|  
|[CComControlBase::GetAmbientRightToLeft](../Topic/CComControlBase::GetAmbientRightToLeft.md)|Recupera **DISPID\_AMBIENT\_RIGHTTOLEFT**, la dirección en que de contenido se muestra en el contenedor.|  
|[CComControlBase::GetAmbientScaleUnits](../Topic/CComControlBase::GetAmbientScaleUnits.md)|Recupera **DISPID\_AMBIENT\_SCALEUNITS**, las unidades de ambiente del contenedor \(como pulgadas o centímetros\) para etiquetar muestran.|  
|[CComControlBase::GetAmbientShowGrabHandles](../Topic/CComControlBase::GetAmbientShowGrabHandles.md)|Recupera **DISPID\_AMBIENT\_SHOWGRABHANDLES**, una marca que indica si el contenedor permite que el control muestre los controladores de arrastre para sí mismo cuando está activo.|  
|[CComControlBase::GetAmbientShowHatching](../Topic/CComControlBase::GetAmbientShowHatching.md)|Recupera **DISPID\_AMBIENT\_SHOWHATCHING**, una marca que indica si el contenedor permite que el control se muestra con un modelo tramado cuando la interfaz de usuario está activa.|  
|[CComControlBase::GetAmbientSupportsMnemonics](../Topic/CComControlBase::GetAmbientSupportsMnemonics.md)|Recupera **DISPID\_AMBIENT\_SUPPORTSMNEMONICS**, una marca que indica si el contenedor admite aceleradoras de teclado.|  
|[CComControlBase::GetAmbientTextAlign](../Topic/CComControlBase::GetAmbientTextAlign.md)|Recupera **DISPID\_AMBIENT\_TEXTALIGN**, la alineación del texto preferido por el contenedor: 0 para la alineación general \(números derecha, texto está\), 1 para la alineación izquierda, 2 para la alineación central, y 3 para la alineación correcta.|  
|[CComControlBase::GetAmbientTopToBottom](../Topic/CComControlBase::GetAmbientTopToBottom.md)|Recupera **DISPID\_AMBIENT\_TOPTOBOTTOM**, la dirección en que de contenido se muestra en el contenedor.|  
|[CComControlBase::GetAmbientUIDead](../Topic/CComControlBase::GetAmbientUIDead.md)|Recupera **DISPID\_AMBIENT\_UIDEAD**, una marca que indica si el contenedor que el control para responder a las acciones de la interfaz de usuario.|  
|[CComControlBase::GetAmbientUserMode](../Topic/CComControlBase::GetAmbientUserMode.md)|Recupera **DISPID\_AMBIENT\_USERMODE**, una marca que indica si el contenedor está en modo de ejecución \(**TRUE**\) o el modo de diseño \(**FALSO**\).|  
|[CComControlBase::GetDirty](../Topic/CComControlBase::GetDirty.md)|Devuelve el valor del miembro de datos `m_bRequiresSave`.|  
|[CComControlBase::GetZoomInfo](../Topic/CComControlBase::GetZoomInfo.md)|Recupera el x y los valores de y del numerador y el denominador del factor de zoom para un control se genera para la edición en contexto.|  
|[CComControlBase::InPlaceActivate](../Topic/CComControlBase::InPlaceActivate.md)|Hace que el control a la transición del estado inactivo cualquier estado el verbo de `iVerb` indica.|  
|[CComControlBase::InternalGetSite](../Topic/CComControlBase::InternalGetSite.md)|Llame a este método para ver el sitio del control para un puntero a la interfaz identificada.|  
|[CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md)|Invalide este método para dibujar el control.|  
|[CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)|**OnDrawAdvanced** predeterminado prepara un contexto normalizado de dispositivos para dibujar, llamar al método de `OnDraw` de su clase de control.|  
|[CComControlBase::OnKillFocus](../Topic/CComControlBase::OnKillFocus.md)|Comprueba que el control está activo en contexto y tiene un sitio válido de control, se informa al contenedor del control ha perdido el foco.|  
|[CComControlBase::OnMouseActivate](../Topic/CComControlBase::OnMouseActivate.md)|Comprueba que la interfaz de usuario está en modo usuario, después activa el control.|  
|[CComControlBase::OnPaint](../Topic/CComControlBase::OnPaint.md)|Prepara el contenedor para pintar, obtiene el área cliente de control, se llama al método de `OnDraw` de la clase del control.|  
|[CComControlBase::OnSetFocus](../Topic/CComControlBase::OnSetFocus.md)|Comprueba que el control está activo en contexto y tiene un sitio válido de control, se informa al contenedor del control ha ganado el foco.|  
|[CComControlBase::PreTranslateAccelerator](../Topic/CComControlBase::PreTranslateAccelerator.md)|Invalide este método para proporcionar dispone de controladores de aceleradores de teclado.|  
|[CComControlBase::SendOnClose](../Topic/CComControlBase::SendOnClose.md)|Notifica a todos los receptores asesores registrados con el marcador advise que se ha cerrado el control.|  
|[CComControlBase::SendOnDataChange](../Topic/CComControlBase::SendOnDataChange.md)|Notifica a todos los receptores asesores registrados con el marcador advise que los datos del control ha cambiado.|  
|[CComControlBase::SendOnRename](../Topic/CComControlBase::SendOnRename.md)|Notifica a todos los receptores asesores registrados con el marcador advise que el control tiene un nuevo moniker.|  
|[CComControlBase::SendOnSave](../Topic/CComControlBase::SendOnSave.md)|Notifica a todos los receptores asesores registrados con el marcador advise que se ha guardado el control.|  
|[CComControlBase::SendOnViewChange](../Topic/CComControlBase::SendOnViewChange.md)|Notifica a todos los receptores asesores registrados que la vista de control ha cambiado.|  
|[CComControlBase::SetControlFocus](../Topic/CComControlBase::SetControlFocus.md)|Establece o quita el foco de teclado a o desde el control.|  
|[CComControlBase::SetDirty](../Topic/CComControlBase::SetDirty.md)|Establezca el miembro de datos `m_bRequiresSave` al valor en `bDirty`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControlBase::m\_bAutoSize](../Topic/CComControlBase::m_bAutoSize.md)|El mensaje que indica el control no puede ser ningún otro tamaño.|  
|[CComControlBase::m\_bDrawFromNatural](../Topic/CComControlBase::m_bDrawFromNatural.md)|Marcador que indica que `IDataObjectImpl::GetData` y `CComControlBase::GetZoomInfo` deben establecer el tamaño del control de `m_sizeNatural` en lugar de `m_sizeExtent`.|  
|[CComControlBase::m\_bDrawGetDataInHimetric](../Topic/CComControlBase::m_bDrawGetDataInHimetric.md)|Marcador que indica que `IDataObjectImpl::GetData` debe utilizar unidades y no los píxeles de HIMETRIC al dibujar.|  
|[CComControlBase::m\_bInPlaceActive](../Topic/CComControlBase::m_bInPlaceActive.md)|El mensaje que indica el control está activo en contexto.|  
|[CComControlBase::m\_bInPlaceSiteEx](../Topic/CComControlBase::m_bInPlaceSiteEx.md)|El mensaje que indica el contenedor admite las características de la interfaz de **IOleInPlaceSiteEx** y control de OR CX96, como controles sin ventana y libres de centelleo.|  
|[CComControlBase::m\_bNegotiatedWnd](../Topic/CComControlBase::m_bNegotiatedWnd.md)|Marcador que indica si el control ha negociado con el contenedor de compatibilidad con las características de control de OR CX96 \(como controles libres de centelleo y sin ventana\), y si el control es con o sin ventana.|  
|[CComControlBase::m\_bRecomposeOnResize](../Topic/CComControlBase::m_bRecomposeOnResize.md)|El mensaje que indica el control desea recomponer la presentación cuando el contenedor cambia el tamaño de presentación del control.|  
|[CComControlBase::m\_bRequiresSave](../Topic/CComControlBase::m_bRequiresSave.md)|El marcador que indique el control ha cambiado desde que se guarda en último lugar.|  
|[CComControlBase::m\_bResizeNatural](../Topic/CComControlBase::m_bResizeNatural.md)|El mensaje que indica el control desea cambiar el tamaño de la extensión natural \(su tamaño físico identifique\) cuando el contenedor cambia el tamaño de presentación del control.|  
|[CComControlBase::m\_bUIActive](../Topic/CComControlBase::m_bUIActive.md)|El mensaje que indica la interfaz de usuario del control, como menús y barras de herramientas, está activo.|  
|[CComControlBase::m\_bUsingWindowRgn](../Topic/CComControlBase::m_bUsingWindowRgn.md)|El mensaje que indica el control utiliza la región contenedor\- proporcionada de la ventana.|  
|[CComControlBase::m\_bWasOnceWindowless](../Topic/CComControlBase::m_bWasOnceWindowless.md)|El marcador que indique el control ha sido sin ventana, pero puede o no puede ser sin ventana ahora.|  
|[CComControlBase::m\_bWindowOnly](../Topic/CComControlBase::m_bWindowOnly.md)|El mensaje que indica el control debe windowed, aunque el contenedor admite controles sin ventana.|  
|[CComControlBase::m\_bWndLess](../Topic/CComControlBase::m_bWndLess.md)|El mensaje que indica el control es sin ventana.|  
|[CComControlBase::m\_hWndCD](../Topic/CComControlBase::m_hWndCD.md)|Contiene una referencia al identificador de ventana asociado al control.|  
|[CComControlBase::m\_nFreezeEvents](../Topic/CComControlBase::m_nFreezeEvents.md)|El número de veces el contenedor ha inmovilizado los eventos \(rechazados para aceptar eventos\) sin reanudar un intermedia de los eventos \(aceptación de eventos\).|  
|[CComControlBase::m\_rcPos](../Topic/CComControlBase::m_rcPos.md)|La posición en píxeles del control, expresados en coordenadas del contenedor.|  
|[CComControlBase::m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)|Extensión del control en unidades de HIMETRIC \(cada unidad es 0,01 milímetros\) para una presentación determinada.|  
|[CComControlBase::m\_sizeNatural](../Topic/CComControlBase::m_sizeNatural.md)|El tamaño físico del control en unidades de HIMETRIC \(cada unidad es 0,01 milímetros\).|  
|[CComControlBase::m\_spAdviseSink](../Topic/CComControlBase::m_spAdviseSink.md)|Un puntero directo a la conexión asesor en el contenedor \( [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)de contenedor\).|  
|[CComControlBase::m\_spAmbientDispatch](../Topic/CComControlBase::m_spAmbientDispatch.md)|Un objeto de `CComDispatchDriver` que le permite recuperar y establecer las propiedades del contenedor a través de un puntero de `IDispatch` .|  
|[CComControlBase::m\_spClientSite](../Topic/CComControlBase::m_spClientSite.md)|Un puntero al sitio del control en el contenedor.|  
|[CComControlBase::m\_spDataAdviseHolder](../Topic/CComControlBase::m_spDataAdviseHolder.md)|Proporciona medios de un estándar de contener conexiones asesores entre los objetos de datos y de advertir a los destinatarios.|  
|[CComControlBase::m\_spInPlaceSite](../Topic/CComControlBase::m_spInPlaceSite.md)|Un puntero puntero a la interfaz de [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), de [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), o de [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) del contenedor.|  
|[CComControlBase::m\_spOleAdviseHolder](../Topic/CComControlBase::m_spOleAdviseHolder.md)|Proporciona una implementación estándar de una manera de contener conexiones asesores.|  
  
## Comentarios  
 Esta clase proporciona métodos para crear y administrar controles ATL.  [clase de CComControl](../../atl/reference/ccomcontrol-class.md) deriva de `CComControlBase`.  Cuando crea un control estándar o un control DHTML mediante el asistente para controles ATL, el asistente automáticamente derivará la clase de `CComControlBase`.  
  
 Para obtener más información sobre cómo crear un control, vea [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  Para obtener más información sobre el asistente para proyectos ATL, vea el artículo [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)