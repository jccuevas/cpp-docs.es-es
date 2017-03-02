---
title: Clase COleControlContainer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleControlContainer
dev_langs:
- C++
helpviewer_keywords:
- custom controls [MFC], sites
- COleControlContainer class
- ActiveX control containers [C++], control site
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
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
ms.openlocfilehash: 764583d28bf71319eac5b7e51e0915ae786261a7
ms.lasthandoff: 02/24/2017

---
# <a name="colecontrolcontainer-class"></a>Clase COleControlContainer
Actúa como contenedor de control para controles ActiveX.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleControlContainer : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Construye un objeto `COleControlContainer`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Crea un sitio del control hospedado por el contenedor.|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informa a hospedado todos los controles que ha cambiado una propiedad de ambiente.|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifica el control de botón especificado.|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Selecciona el botón de radio especificado de un grupo.|  
|[COleControlContainer::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|  
|[COleControlContainer::CreateOleFont](#createolefont)|Crea una fuente OLE.|  
|[COleControlContainer::FindItem](#finditem)|Devuelve el sitio personalizado del control especificado.|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Determina si el sitio del control es aceptar eventos.|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|Recupera la propiedad de ambiente especificada.|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|Recupera el control de cuadro de diálogo especificado.|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Recupera el valor del control de cuadro de diálogo especificado.|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Recupera el título del control de cuadro de diálogo especificado.|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Determina si el contenedor controla `WM_SETFOCUS` mensajes.|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Controla los mensajes enviados a un control sin ventanas.|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Determina el estado del botón especificado.|  
|[COleControlContainer::OnPaint](#onpaint)|Se llama para dibujar una parte del contenedor.|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|Se llama cuando un control está a punto de ser activado en contexto.|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Se llama cuando un control está a punto de desactivarse.|  
|[COleControlContainer::ScrollChildren](#scrollchildren)|Llamado por el marco de trabajo cuando se reciben mensajes de desplazamiento de una ventana secundaria.|  
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envía un mensaje al control especificado.|  
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Establece el valor del control especificado.|  
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Establece el texto del control especificado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControlContainer::m_crBack](#m_crback)|El color de fondo del contenedor.|  
|[COleControlContainer::m_crFore](#m_crfore)|El color de primer plano del contenedor.|  
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Una lista de los sitios de control compatibles.|  
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|El número de controles sin ventana hospedados.|  
|[COleControlContainer::m_pOleFont](#m_polefont)|Puntero a la fuente OLE de sitio del control personalizado.|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Puntero al sitio del control de captura.|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Puntero al control que actualmente tiene el foco de entrada.|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Puntero al control que está actualmente activado en el contexto.|  
|[COleControlContainer::m_pWnd](#m_pwnd)|Puntero a la ventana implementar el contenedor del control.|  
|[COleControlContainer::m_siteMap](#m_sitemap)|El mapa del sitio.|  
  
## <a name="remarks"></a>Comentarios  
 Esto se hace proporcionando compatibilidad para uno o varios sitios de control ActiveX (implementado por `COleControlSite`). `COleControlContainer`implementa totalmente el [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) y [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) interfaces, lo que permite a los controles ActiveX contenidos satisfacer sus requisitos como elementos en el contexto.  
  
 Normalmente, esta clase se utiliza junto con `COccManager` y `COleControlSite` para implementar un contenedor de controles ActiveX personalizado, con los sitios personalizados para uno o más controles de ActiveX.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxocc.h  
  
##  <a name="a-nameattachcontrolsitea--colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite  
 Llamado por el marco para crear y asociar un sitio del control.  
  
```  
virtual void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);

 
void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero a un `CWnd` objeto.  
  
 `nIDC`  
 El identificador del control que se adjuntará.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea personalizar este proceso.  
  
> [!NOTE]
>  Utilice la primera forma de esta función si se vincula estáticamente a la biblioteca MFC. Utilice el segundo formulario si vincula dinámicamente la biblioteca MFC.  
  
##  <a name="a-namebroadcastambientpropertychangea--colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange  
 Informa a hospedado todos los controles que ha cambiado una propiedad de ambiente.  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de la propiedad de ambiente que se va a cambiar.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función cuando una propiedad de ambiente ha cambiado el valor. Reemplazar esta función para personalizar este comportamiento.  
  
##  <a name="a-namecheckdlgbuttona--colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton  
 Modifica el estado actual del botón.  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDButton`  
 El identificador del botón que se va a modificar.  
  
 `nCheck`  
 Especifica el estado del botón. Puede ser uno de los siguientes:  
  
- **BST_CHECKED** establece el estado del botón.  
  
- **BST_INDETERMINATE** establece el estado del botón en gris, que indica un estado indeterminado. Utilice este valor sólo si el botón tiene el **BS_3STATE** o **BS_AUTO3STATE** estilo.  
  
- **BST_UNCHECKED** establece el estado del botón en desactivada.  
  
##  <a name="a-namecheckradiobuttona--colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton  
 Selecciona un botón de opción especificado en un grupo y borra los botones restantes en el grupo.  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDFirstButton`  
 Especifica el identificador del primer botón de radio del grupo.  
  
 `nIDLastButton`  
 Especifica el identificador del último botón de radio del grupo.  
  
 `nIDCheckButton`  
 Especifica el identificador del botón de radio que se va a comprobar.  
  
##  <a name="a-namecolecontrolcontainera--colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer  
 Construye un objeto `COleControlContainer`.  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana primaria del contenedor del control.  
  
### <a name="remarks"></a>Comentarios  
 Una vez que se ha creado correctamente el objeto, agregar un sitio de control personalizado con una llamada a `AttachControlSite`.  
  
##  <a name="a-namecreatecontrola--colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl  
 Crea un control ActiveX, hospedado por especificado `COleControlSite` objeto.  
  
```  
BOOL CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist =NULL,  
    BOOL bStorage =FALSE,  
    BSTR bstrLicKey =NULL,  
    COleControlSite** ppNewSite =NULL);

 
BOOL CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist =NULL,  
    BOOL bStorage =FALSE,  
    BSTR bstrLicKey =NULL,  
    COleControlSite** ppNewSite =NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndCtrl`  
 Un puntero al objeto window que representa el control.  
  
 `clsid`  
 El identificador de clase único del control.  
  
 `lpszWindowName`  
 Puntero al texto que se mostrará en el control. Establece el valor de propiedad de título o el texto del control (si existe). Si **NULL**, no se cambia la propiedad de título o el texto del control.  
  
 `dwStyle`  
 Estilos de Windows. Los estilos disponibles se enumeran en la **comentarios** sección.  
  
 `rect`  
 Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `nID`  
 Especifica el identificador de ventana secundaria del control  
  
 `pPersist`  
 Un puntero a un `CFile` que contiene el estado persistente del control. El valor predeterminado es **NULL**, que indica que el control se inicializa sin restaurar su estado desde el almacenamiento persistente. Si no **NULL**, debe ser un puntero a un `CFile`-objeto que contiene los datos persistentes del control, en forma de una secuencia o un almacenamiento derivado. Estos datos podrían guardados en una activación anterior del cliente. El `CFile` puede contener otros datos, pero debe tener su puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada a `CreateControl`.  
  
 `bStorage`  
 Indica si los datos de `pPersist` debe interpretarse como `IStorage` o `IStream` datos. Si los datos de `pPersist` es un almacenamiento `bStorage` debe ser **TRUE**. Si los datos de `pPersist` es una secuencia, `bStorage` debe ser **FALSE**. El valor predeterminado es **FALSE**.  
  
 `bstrLicKey`  
 Datos de clave de licencia opcional. Estos datos sólo es necesaria para crear controles que requieren una clave de licencia de tiempo de ejecución. Si el control admite licencias, debe proporcionar una clave de licencia para la creación del control que se realice correctamente. El valor predeterminado es **NULL**.  
  
 *ppNewSite*  
 Un puntero al sitio del control existente que va a hospedar el control que se va a crear. El valor predeterminado es **NULL**, que indica que un nuevo sitio de control automáticamente y se adjunta al nuevo control.  
  
 `ppt`  
 Un puntero a un **punto** estructura que contiene la esquina superior izquierda del control. El tamaño del control se determina por el valor de *psize*. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y la posición del control.  
  
 *psize*  
 Un puntero a un **tamaño** estructura que contiene el tamaño del control. La esquina superior izquierda se determina por el valor de `ppt`. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y la posición del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Sólo un subconjunto de las ventanas `dwStyle` marcas son compatibles con `CreateControl`:  
  
- **WS_VISIBLE** crea una ventana que esté visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como las ventanas normales.  
  
- **WS_DISABLED** crea una ventana que está inicialmente deshabilitada. Una ventana deshabilitada no puede recibir entradas del usuario. Se puede establecer si el control tiene la propiedad Enabled.  
  
- `WS_BORDER`Crea una ventana con un borde de línea fina. Se puede establecer si el control tiene una propiedad de estilo de borde.  
  
- **WS_GROUP** especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control en el grupo a otro mediante las teclas de dirección. Todos los controles definidos con el **WS_GROUP** después de que el primer control pertenecen al mismo grupo de estilos. El siguiente control con el **WS_GROUP** estilo finaliza el grupo y comienza el siguiente grupo.  
  
- **WS_TABSTOP** especifica un control que puede recibir el foco de teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB cambia el foco del teclado al siguiente control de la **WS_TABSTOP** estilo.  
  
 Usar la segunda sobrecarga para crear controles de tamaño predeterminado.  
  
##  <a name="a-namecreateolefonta--colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont  
 Crea una fuente OLE.  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 Puntero a la fuente que va a usar el contenedor del control.  
  
##  <a name="a-namefinditema--colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem  
 Busca el sitio personalizado que hospeda el elemento especificado.  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del elemento que se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio personalizado del elemento especificado.  
  
##  <a name="a-namefreezealleventsa--colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents  
 Determina si el contenedor se omita algunos eventos desde los sitios de control adjunto o aceptarlos.  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFreeze`  
 Distinto de cero si se procesarán los eventos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control no es necesario detener el desencadenamiento de eventos si solicitado por el contenedor del control. Puede continuar la activación pero se omitirá todos los eventos subsiguientes en el contenedor del control.  
  
##  <a name="a-namegetambientpropa--colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp  
 Recupera el valor de una propiedad de ambiente especificada.  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSite`  
 Puntero a un sitio de control desde el que se recuperará la propiedad de ambiente.  
  
 `dispid`  
 El identificador de envío de la propiedad de ambiente deseada.  
  
 *pVarResult*  
 Un puntero al valor de la propiedad de ambiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namegetdlgitema--colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem  
 Recupera un puntero a la ventana de control o elemento secundario especificada en un cuadro de diálogo u otra ventana.  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Identificador del elemento de cuadro de diálogo para recuperar.  
  
 `phWnd`  
 Puntero al identificador del objeto de la ventana del elemento de cuadro de diálogo especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana del elemento de cuadro de diálogo.  
  
##  <a name="a-namegetdlgiteminta--colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt  
 Recupera el valor del texto traducido del control dado.  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control.  
  
 `lpTrans`  
 Puntero a una variable booleana que recibe un valor de función correcto o con errores ( **TRUE** indica éxito, **FALSE** indica un error).  
  
 `bSigned`  
 Especifica si la función debe examinar el texto de un signo menos al principio y devolver un valor entero con signo si encuentra alguno. Si el `bSigned` parámetro es **TRUE**, especificando que el valor que se va a recuperar un valor entero con signo, convertir el valor devuelto para una `int` tipo. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, la variable señala `lpTrans` está establecido en **TRUE**, y el valor devuelto es el valor traducido del texto del control.  
  
 Si se produce un error en la función, la variable señala `lpTrans` está establecido en **FALSE**, y el valor devuelto es cero. Tenga en cuenta que, desde cero es un posible valor traducido, un valor devuelto de cero indica error.  
  
 Si `lpTrans` es **NULL**, la función no devuelve ninguna información sobre el éxito o error.  
  
### <a name="remarks"></a>Comentarios  
 La función traduce el texto recuperado por la eliminación de todos los espacios adicionales al principio del texto y, a continuación, convertir los dígitos decimales. La función deja traducir cuando llega al final del texto o se encuentra un carácter numérico.  
  
 Esta función devuelve cero si el valor convertido es mayor que **INT_MAX** (para números con signo) o **UINT_MAX** (para los números sin signo).  
  
##  <a name="a-namegetdlgitemtexta--colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText  
 Recupera el texto del control dado.  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control.  
  
 `lpStr`  
 Puntero al texto del control.  
  
 `nMaxCount`  
 Especifica la longitud máxima, en caracteres, de la cadena se copien en el búfer señalado por `lpStr`. Si la longitud de la cadena supera el límite, se trunca la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto especifica el número de caracteres copiados en el búfer, sin incluir el carácter nulo de terminación.  
  
 Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
##  <a name="a-namehandlesetfocusa--colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus  
 Determina si el contenedor controla `WM_SETFOCUS` mensajes.  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el contenedor controla `WM_SETFOCUS` mensajes; en caso contrario, cero.  
  
##  <a name="a-namehandlewindowlessmessagea--colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage  
 Procesa los mensajes de ventana para los controles sin ventana.  
  
```  
virtual BOOL HandleWindowlessMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam,  
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `message`  
 El identificador para el mensaje de ventana proporcionado por Windows.  
  
 `wParam`  
 Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la `message` parámetro.  
  
 `lParam`  
 Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la `message` parámetro.  
  
 *plResult*  
 Código de resultado de Windows. Especifica el resultado del procesamiento del mensaje y depende del mensaje enviado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el control de mensajes de control sin ventana.  
  
##  <a name="a-nameisdlgbuttoncheckeda--colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked  
 Determina el estado del botón especificado.  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDButton`  
 El identificador del control de botón.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto de un botón creado con el **BS_AUTOCHECKBOX**, **BS_AUTORADIOBUTTON**, **BS_AUTO3STATE**, **BS_CHECKBOX**, **BS_RADIOBUTTON**, o **BS_3STATE** estilo. Puede ser uno de los siguientes:  
  
- **BST_CHECKED** se activa el botón.  
  
- **BST_INDETERMINATE** botón aparece atenuado, lo que indica un estado indeterminado (se aplica sólo si el botón tiene el **BS_3STATE** o **BS_AUTO3STATE** estilo).  
  
- **BST_UNCHECKED** botón está desactivado.  
  
### <a name="remarks"></a>Comentarios  
 Si el botón es un control de tres estados, la función miembro determina si se está atenuado, activa, o ninguno.  
  
##  <a name="a-namemcrbacka--colecontrolcontainermcrback"></a><a name="m_crback"></a>COleControlContainer::m_crBack  
 El color de fondo del contenedor.  
  
```  
COLORREF m_crBack;  
```  
  
##  <a name="a-namemcrforea--colecontrolcontainermcrfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore  
 El color de primer plano del contenedor.  
  
```  
COLORREF m_crFore;  
```  
  
##  <a name="a-namemlistsitesorwndsa--colecontrolcontainermlistsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds  
 Una lista de los sitios de control hospedado por el contenedor.  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="a-namemnwindowlesscontrolsa--colecontrolcontainermnwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls  
 El número de controles sin ventana hospedada por el contenedor del control.  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="a-namempolefonta--colecontrolcontainermpolefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont  
 Puntero a la fuente OLE de sitio del control personalizado.  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="a-namempsitecapturea--colecontrolcontainermpsitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture  
 Puntero al sitio del control de captura.  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="a-namempsitefocusa--colecontrolcontainermpsitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus  
 Un puntero al sitio del control que actualmente tiene el foco de entrada.  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="a-namempsiteuiactivea--colecontrolcontainermpsiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive  
 Un puntero al sitio del control que está activado en el contexto.  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="a-namempwnda--colecontrolcontainermpwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd  
 Un puntero al objeto de ventana asociado al contenedor.  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="a-namemsitemapa--colecontrolcontainermsitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap  
 El mapa del sitio.  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="a-nameonpainta--colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint  
 Llamado por el marco para controlar `WM_PAINT` solicitudes.  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero al contexto de dispositivo utilizado por el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el mensaje; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el proceso de dibujo.  
  
##  <a name="a-nameonuiactivatea--colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate  
 Llamado por el marco de trabajo cuando el sitio del control, que señala `pSite`, está a punto de activar en contexto.  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSite`  
 Un puntero al sitio del control va a activar en contexto.  
  
### <a name="remarks"></a>Comentarios  
 Activación en contexto significa que el menú del contenedor principal se reemplaza con un menú compuesto de in situ.  
  
##  <a name="a-nameonuideactivatea--colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate  
 Llamado por el marco de trabajo cuando el sitio del control, que señala `pSite`, está a punto de desactivarse.  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSite`  
 Un puntero al sitio del control va a desactivar.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se recibe esta notificación, el contenedor debe volver a instalar la interfaz de usuario y recibir el foco.  
  
##  <a name="a-namescrollchildrena--colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren  
 Llamado por el marco de trabajo cuando se reciben mensajes de desplazamiento de una ventana secundaria.  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>Parámetros  
 `dx`  
 La cantidad, en píxeles, de desplazamiento en el eje x.  
  
 *dy*  
 La cantidad, en píxeles, de desplazamiento a lo largo del eje y.  
  
##  <a name="a-namesenddlgitemmessagea--colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage  
 Envía un mensaje al control especificado.  
  
```  
virtual LRESULT SendDlgItemMessage(
    int nID,  
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Especifica el identificador del control que recibe el mensaje.  
  
 `message`  
 Especifica que se envíe el mensaje.  
  
 `wParam`  
 Especifica información adicional específica del mensaje.  
  
 `lParam`  
 Especifica información adicional específica del mensaje.  
  
##  <a name="a-namesetdlgiteminta--colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt  
 Establece el texto de un control en un cuadro de diálogo para la representación de cadena de un valor entero especificado.  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control.  
  
 `nValue`  
 El valor entero que se mostrará.  
  
 `bSigned`  
 Especifica si el `nValue` parámetro es con o sin signo. Si este parámetro es **TRUE**, `nValue` está firmado. Si este parámetro es **TRUE** y `nValue` es menor que cero, un inicio de sesión se coloca antes del primer dígito en la cadena de menos. Si este parámetro es **FALSE**, `nValue` es sin signo.  
  
##  <a name="a-namesetdlgitemtexta--colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText  
 Establece el texto del control especificado, con el texto contenido en `lpszString`.  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control.  
  
 `lpszString`  
 Puntero al texto del control.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [Clase COccManager](../../mfc/reference/coccmanager-class.md)

