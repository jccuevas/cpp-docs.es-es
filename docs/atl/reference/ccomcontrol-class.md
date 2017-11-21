---
title: Clase CComControl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs: C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ddbd18ac39721dd80eb547e53c7708891b94aa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcontrol-class"></a>Clase CComControl
Esta clase proporciona métodos para crear y administrar los controles ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase que implementa el control.  
  
 *WinBase*  
 La clase base que implementa funciones basadas en ventanas. Valor predeterminado es [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crea una ventana para el control.|  
|[CComControl::FireOnChanged](#fireonchanged)|Notifica a los receptores del contenedor que ha cambiado una propiedad de control.|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifica a los receptores del contenedor que una propiedad de control se va a cambiar y que el objeto está solicitando el receptor cómo continuar.|  
|[CComControl::MessageBox](#messagebox)|Llame a este método para crear, mostrar y trabajar con un cuadro de mensaje.|  
  
## <a name="remarks"></a>Comentarios  
 `CComControl`es un conjunto de funciones auxiliares de control útil y miembros de datos esenciales para los controles ATL. Cuando se crea un control estándar o un control DHTML mediante el Asistente para controles ATL, el asistente automáticamente derivará la clase de `CComControl`. `CComControl`deriva la mayoría de sus métodos de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Para obtener más información acerca de cómo crear un control, vea el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Para ver una demostración de `CComControl` métodos y miembros de datos, vea el [CIRC](../../visual-cpp-samples.md) ejemplo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="ccomcontrol"></a>CComControl::CComControl  
 El constructor.  
  
```
CComControl();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas a la [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) constructor y le pasa el `m_hWnd` hereda el miembro de datos a través de [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz que se solicita.  
  
 `ppv`  
 [out] Un puntero al puntero de interfaz identificado por `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="remarks"></a>Comentarios  
 Solo administra interfaces de la tabla de asignación COM.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow  
 De forma predeterminada, crea una ventana para el control mediante una llamada a `CWindowImpl::Create`.  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 [in] Identificador de la ventana primaria o propietaria. Se debe suministrar un identificador de ventana válido. La ventana de control se limita al área de su ventana primaria.  
  
 `rcPos`  
 [in] El tamaño inicial y la posición de la ventana que se va a crear.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea hacer algo distinto de crear una sola ventana, por ejemplo, para crear dos ventanas, uno de los cuales se convierte en una barra de herramientas para el control.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>CComControl::FireOnChanged  
 Notifica a los receptores del contenedor que ha cambiado una propiedad de control.  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dispID*  
 [in] Identificador de la propiedad que ha cambiado.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase del control se deriva de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), llama a este método [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) notificar todos conectados `IPropertyNotifySink` interfaces que el control especificado propiedad ha cambiado. Si la clase del control no se deriva de `IPropertyNotifySink`, este método devuelve `S_OK`. 
  
 Este método es seguro llamar a incluso si el control no admite puntos de conexión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit  
 Notifica a los receptores del contenedor que una propiedad de control se va a cambiar y que el objeto está solicitando el receptor cómo continuar.  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dispID*  
 [in] Identificador de la propiedad que se va a cambiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la clase del control se deriva de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), llama a este método [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) notificar todos conectados `IPropertyNotifySink` interfaces que el especificado propiedad de control que se va a cambiar. Si la clase del control no se deriva de `IPropertyNotifySink`, este método devuelve `S_OK`.  

  
 Este método es seguro llamar a incluso si el control no admite puntos de conexión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>CComControl::MessageBox  
 Llame a este método para crear, mostrar y trabajar con un cuadro de mensaje.  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 El texto que se mostrará en el cuadro de mensaje.  
  
 `lpszCaption`  
 El título del cuadro de diálogo. Si es NULL (valor predeterminado), el título "Error" se utiliza.  
  
 `nType`  
 Especifica el contenido y el comportamiento del cuadro de diálogo. Consulte la [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) entrada en la documentación del SDK de Windows para obtener una lista de los cuadros de mensaje diferentes disponibles. El valor predeterminado proporciona un sencillo **Aceptar** botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de entero que especifica uno de los valores de elemento de menú que aparecen en [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) en la documentación del SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 `MessageBox`es útil durante el desarrollo y una manera sencilla de mostrar un error o mensaje de advertencia al usuario.  
  
## <a name="see-also"></a>Vea también  
 [Clase de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clase CComControlBase](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl (clase)](../../atl/reference/ccomcompositecontrol-class.md)
