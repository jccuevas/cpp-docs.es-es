---
title: "Clase Cnetdirecciónctrl | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CNetAddressCtrl class
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: 32
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
ms.openlocfilehash: 03b08d13a9e456c5533b4dddce7f389a63a69c6d
ms.lasthandoff: 02/24/2017

---
# <a name="cnetaddressctrl-class"></a>Clase CNetDirecciónCtrl
La clase `CNetAddressCtrl` representa el control de dirección de red, que puede utilizar para especificar y validar el formato de direcciones IPv4, IPv6 y DNS con nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CNetAddressCtrl : public CEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Construye un objeto `CNetAddressCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CNetAddressCtrl::Create](#create)|Crea un control de dirección de red con los estilos especificados y lo adjunta a la corriente `CNetAddressCtrl` objeto.|  
|[CNetAddressCtrl::CreateEx](#createex)|Crea un control de dirección de red con estilos extendidos especificados y lo adjunta a la corriente `CNetAddressCtrl` objeto.|  
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Muestra un globo de información de error cuando el usuario escribe una dirección de red no compatible en el control de dirección de red actual.|  
|[CNetAddressCtrl::GetAddress](#getaddress)|Recupera una representación analizada y validar la dirección de red asociada con el control de dirección de red actual.|  
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.|  
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.|  
  
## <a name="remarks"></a>Comentarios  
 El control de dirección de red, se comprueba que el formato de la dirección que el usuario escribe es correcto. El control no conectar realmente a la dirección de red. El [CNetAddressCtrl::SetAllowType](#setallowtype) método especifica uno o más tipos de dirección que el [CNetAddressCtrl::GetAddress](#getaddress) puede analizar y comprobar el método. Puede ser una dirección en el formulario de IPv4, IPv6 o dirección con nombre para un servidor, la red, el host o el destino de los mensajes de difusión. Si el formato de la dirección es correcto, puede utilizar el [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un cuadro de mensaje de recuadro informativo que señala al cuadro de texto del control de dirección de red gráficamente y muestra un mensaje de error predefinidas.  
  
 El `CNetAddressCtrl` clase se deriva de la [CEdit](../../mfc/reference/cedit-class.md) clase. Por consiguiente, el control de dirección de red proporciona acceso a todos los mensajes de control de edición de Windows.  
  
 La figura siguiente muestra un cuadro de diálogo que contiene un control de dirección de red. El texto cuadro (1) para el control de dirección de red contiene una dirección de red no válido. Si la dirección de red no es válida, se muestra el mensaje de recuadro informativo (2).  
  
 ![Cuadro de diálogo con un control de dirección de red y un recuadro informativo. ] (../../mfc/reference/media/cnetaddctrl.png "cnetaddctrl")  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente es una parte de un cuadro de diálogo que valida una dirección de red. Los controladores de eventos para los tres botones de radio especifican que la dirección de red puede ser uno de los tres tipos de direcciones. El usuario escribe una dirección en el cuadro de texto del control de la red, a continuación, presiona un botón para validar la dirección. Si la dirección es válida, se muestra un mensaje de confirmación; de lo contrario, se muestra el mensaje de error predefinidos de recuadro informativo.  
  
 [!code-cpp[1 NVC_MFC_CNetAddressCtrl_s1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código del archivo de encabezado del cuadro de diálogo define la [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) y [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) variables que necesita la [CNetAddressCtrl::GetAddress](#getaddress) (método).  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
 Esta clase es compatible con [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] y versiones posteriores.  
  
 Requisitos adicionales para esta clase se describen en [crear requisitos para Windows Vista controles comunes](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="a-namecnetaddressctrla--cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl  
 Construye un objeto `CNetAddressCtrl`.  
  
```  
CNetAddressCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CNetAddressCtrl::Create](#create) o [CNetAddressCtrl::CreateEx](#createex) método para crear un control de la red y adjuntarlo a la `CNetAddressCtrl` objeto.  
  
##  <a name="a-namecreatea--cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl::Create  
 Crea un control de dirección de red con los estilos especificados y lo adjunta a la corriente `CNetAddressCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwStyle`|Una combinación bit a bit de los estilos que se aplicará al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/edit-styles.md).|  
|[in] `rect`|Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control.|  
|[in] `pParentWnd`|Un puntero no null para un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control.|  
|[in] `nID`|El identificador del control.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
##  <a name="a-namecreateexa--cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl::CreateEx  
 Crea un control de dirección de red con estilos extendidos especificados y lo adjunta a la corriente `CNetAddressCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwExStyle`|Una combinación bit a bit (OR) de los estilos extendidos que se aplicará al control. Para obtener más información, consulte el `dwExStyle` parámetro de la [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) (función).|  
|[in] `dwStyle`|Una combinación bit a bit (OR) de estilos que se aplicará al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/edit-styles.md).|  
|[in] `rect`|Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control.|  
|[in] `pParentWnd`|Un puntero no null para un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control.|  
|[in] `nID`|El identificador del control.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
##  <a name="a-namedisplayerrortipa--cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip  
 Muestra un mensaje de error en el globo de sugerencias asociado al control de dirección de red actual.  
  
```  
HRESULT DisplayErrorTip();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor `S_OK` si este método es correcta; en caso contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones que puede admitir el control de dirección de red actual. Utilice la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Utilice la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si la [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.  
  
 Este mensaje, se invoca el [NetAddr_DisplayErrorTip](http://msdn.microsoft.com/library/windows/desktop/bb774314) (macro), que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Macro envía el `NCM_DISPLAYERRORTIP` mensaje.  
  
##  <a name="a-namegetaddressa--cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl::GetAddress  
 Recupera una representación analizada y validar la dirección de red que está asociada con el control de dirección de red actual.  
  
```  
HRESULT GetAddress(PNC_ADDRESS pAddress) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in, out] `pAddress`|Puntero a un [NC_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) estructura.  Establecer el `pAddrInfo` miembro de esta estructura a la dirección de un [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) estructura antes de llamar al método GetAddress.|  
  
### <a name="return-value"></a>Valor devuelto  
 El valor `S_OK` si este método es correcta; en caso contrario, un código de error COM. Para obtener más información acerca de los códigos de error posibles, consulte la sección de valor devuelto de la [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) (macro).  
  
### <a name="remarks"></a>Comentarios  
 Si este método se realiza correctamente, el [NET_ADDRESS_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) estructura contiene información adicional acerca de la dirección de red.  
  
 Utilice la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones puede admitir el control de dirección de red actual. Utilice la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Utilice la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si la [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.  
  
 Este método invoca el [NetAddr_GetAddress](http://msdn.microsoft.com/library/windows/desktop/bb774316) (macro), que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Macro envía el `NCM_GETADDRESS` mensaje.  
  
##  <a name="a-namegetallowtypea--cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl::GetAllowType  
 Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.  
  
```  
DWORD GetAllowType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación bit a bit (OR) de indicadores que especifica los tipos de direcciones que puede admitir el control de dirección de red. Para obtener más información, consulte [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).  
  
### <a name="remarks"></a>Comentarios  
 Este mensaje, se invoca el [NetAddr_GetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774318) (macro), que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Macro envía el `NCM_GETALLOWTYPE` mensaje.  
  
##  <a name="a-namesetallowtypea--cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl::SetAllowType  
 Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.  
  
```  
HRESULT SetAllowType(DWORD dwAddrMask);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwAddrMask`|Una combinación bit a bit (OR) de indicadores que especifica los tipos de direcciones que puede admitir el control de dirección de red. Para obtener más información, consulte [NET_STRING](http://msdn.microsoft.com/library/windows/desktop/bb762586).|  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`Si este método se realiza correctamente; de lo contrario, un código de error COM.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CNetAddressCtrl::SetAllowType](#setallowtype) método para especificar los tipos de direcciones que puede admitir el control de dirección de red actual. Utilice la [CNetAddressCtrl::GetAddress](#getaddress) método para validar y analizar la dirección de red que el usuario escribe. Utilice la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) método para mostrar un recuadro informativo de mensaje de error si la [CNetAddressCtrl::GetAddress](#getaddress) método es incorrecto.  
  
 Este mensaje, se invoca el [NetAddr_SetAllowType](http://msdn.microsoft.com/library/windows/desktop/bb774320) (macro), que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Macro envía el `NCM_SETALLOWTYPE` mensaje.  
  
## <a name="see-also"></a>Vea también  
 [Clase Cnetdirecciónctrl](../../mfc/reference/cnetaddressctrl-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)

