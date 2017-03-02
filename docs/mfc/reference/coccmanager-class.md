---
title: Clase COccManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COccManager
dev_langs:
- C++
helpviewer_keywords:
- custom controls [MFC], sites
- COccManager class
- CNoTrackObject class
- ActiveX control containers [C++], control site
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 14a75c491a7061d921d6c0c250c6224f4e7d2f04
ms.lasthandoff: 02/24/2017

---
# <a name="coccmanager-class"></a>Clase COccManager
Administra distintos sitios de control personalizado; implementado por objetos `COleControlContainer` y `COleControlSite` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|Crea un **COleContainer** objeto.|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crea los controles ActiveX, hospedados por el asociado `COleContainer` objeto.|  
|[COccManager::CreateSite](#createsite)|Crea un objeto `COleClientSite`.|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|Recupera el código del botón predeterminado.|  
|[COccManager::IsDialogMessage](#isdialogmessage)|Determina el destino de un mensaje de diálogo.|  
|[COccManager::IsLabelControl](#islabelcontrol)|Determina si el control especificado es un control de etiqueta.|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Determina si la tecla de acceso actual coincide con la tecla de acceso del control especificado.|  
|[COccManager::OnEvent](#onevent)|Intenta controlar el evento especificado.|  
|[COccManager::PostCreateDialog](#postcreatedialog)|Libera recursos asignados durante la creación del cuadro de diálogo.|  
|[COccManager::PreCreateDialog](#precreatedialog)|Procesa una plantilla de cuadro de diálogo para controles ActiveX.|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|Alterna el estado predeterminado del control especificado.|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Separa los controles ActiveX existentes de los controles comunes en la plantilla de cuadro de diálogo especificado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase base, **CNoTrackObject**, es una clase base sin documentar (ubicada en AFXTLS. (H). Diseñado para su uso por el marco de trabajo MFC, las clases derivadas de la **CNoTrackObject** clase están exentos de la detección de pérdidas de memoria. Se recomienda no derivar directamente de **CNoTrackObject**.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxocc.h  
  
##  <a name="a-namecreatecontainera--coccmanagercreatecontainer"></a><a name="createcontainer"></a>COccManager::CreateContainer  
 Llamado por el marco para crear un contenedor de control.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero al objeto de ventana asociado al contenedor de sitios personalizados.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contenedor recién creado; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la creación de sitios personalizados, consulte [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="a-namecreatedlgcontrolsa--coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COccManager::CreateDlgControls  
 Llame a esta función para crear controles ActiveX especificados por el `pOccDialogInfo` parámetro.  
  
```  
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    LPCTSTR lpszResourceName,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

 
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,  
    void* lpResource,  
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWndParent*  
 Un puntero al elemento primario del objeto de cuadro de diálogo.  
  
 `lpszResourceName`  
 El nombre del recurso que se va a crear.  
  
 `pOccDialogInfo`  
 Puntero a la plantilla de cuadro de diálogo usada para crear el objeto de cuadro de diálogo.  
  
 `lpResource`  
 Un puntero a un recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control se creó correctamente; en caso contrario, es cero.  
  
##  <a name="a-namecreatesitea--coccmanagercreatesite"></a><a name="createsite"></a>COccManager::CreateSite  
 Llamado por el marco para crear un sitio del control hospedado por el contenedor al que apunta `pCtrlCont`.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCtrlCont`  
 Un puntero al contenedor del control que hospeda el sitio del control nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio del control recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para crear un control personalizado del sitio, con su [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-clase derivada.  
  
 Cada contenedor de control puede hospedar varios sitios. Crear sitios adicionales en varias llamadas a `CreateSite`.  
  
##  <a name="a-namegetdefbtncodea--coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode  
 Llame a esta función para determinar si el control es un botón de comando predeterminado.  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 El objeto de ventana que contiene el control de botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores:  
  
- **DLGC_DEFPUSHBUTTON** Control es el botón predeterminado en el cuadro de diálogo.  
  
- **DLGC_UNDEFPUSHBUTTON** Control no es el botón predeterminado en el cuadro de diálogo.  
  
- **0** control no es un botón.  
  
##  <a name="a-nameisdialogmessagea--coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COccManager::IsDialogMessage  
 Llamado por el marco de trabajo para determinar si un mensaje está pensado para el cuadro de diálogo especificado y, si es así, procesa el mensaje.  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWndDlg*  
 Un puntero al cuadro de diálogo de destino del mensaje.  
  
 `lpMsg`  
 Un puntero a un `MSG` estructura que contiene el mensaje que se va a comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se procesa el mensaje; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado de `IsDialogMessage` es comprobar si hay mensajes de teclado y convertirlos en selecciones en el cuadro de diálogo correspondiente. Por ejemplo, la tecla TAB, cuando se presionan, selecciona el siguiente control o grupo de controles.  
  
 Reemplazar esta función para proporcionar un comportamiento personalizado para los mensajes enviados al cuadro de diálogo especificado.  
  
##  <a name="a-nameislabelcontrola--coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COccManager::IsLabelControl  
 Llame a esta función para determinar si el control especificado es un control de etiqueta.  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control es una etiqueta; en caso contrario cero  
  
### <a name="remarks"></a>Comentarios  
 Un control label es aquel que actúa como una etiqueta para cualquier control que es el siguiente en la ordenación.  
  
##  <a name="a-nameismatchingmnemonica--coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic  
 Llame a esta función para determinar si la tecla de acceso actual coincide con el representado por el control.  
  
```  
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,  
    LPMSG lpMsg);

 
static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene el control.  
  
 `lpMsg`  
 Un puntero al mensaje que contiene la tecla de acceso para hacer coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la tecla de acceso coincide con el control; en caso contrario cero  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoneventa--coccmanageronevent"></a><a name="onevent"></a>COccManager::OnEvent  
 Llamado por el marco de trabajo para controlar el evento especificado.  
  
```  
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,  
    UINT idCtrl,  
    AFX_EVENT* pEvent,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCmdTarget*  
 Un puntero a la `CCmdTarget` intentar controlar el evento de objeto  
  
 `idCtrl`  
 El identificador de recurso del control.  
  
 `pEvent`  
 Evento que se controla.  
  
 `pHandlerInfo`  
 Si no **NULL**, `OnEvent` rellena la **pTarget** y **pmf** los miembros de la **AFX_CMDHANDLERINFO** estructura en lugar de enviar el comando. Normalmente, este parámetro debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se controló el evento, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el proceso de control de eventos predeterminado.  
  
##  <a name="a-nameprecreatedialoga--coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog  
 Llamado por el marco de trabajo para procesar una plantilla de cuadro de diálogo para controles ActiveX antes de crear el cuadro de diálogo real.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles de ActiveX alojados en el cuadro de diálogo.  
  
 *pOrigTemplate*  
 Puntero a la plantilla de cuadro de diálogo que se utilizará para crear el cuadro de diálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una estructura de plantilla de cuadro de diálogo utilizado para crear el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado hace una llamada a `SplitDialogTemplate`, determinar si hay cualquier ActiveX controles presente y, a continuación, devuelve la plantilla de cuadro de diálogo resultante.  
  
 Reemplazar esta función para personalizar el proceso de creación de un cuadro de diálogo hospedar controles ActiveX.  
  
##  <a name="a-namepostcreatedialoga--coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog  
 Llamado por el marco para liberar la memoria asignada para la plantilla de cuadro de diálogo.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles de ActiveX alojados en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Esta memoria se asignó mediante una llamada a `SplitDialogTemplate`y se utiliza para los controles de ActiveX alojados en el cuadro de diálogo.  
  
 Reemplazar esta función para personalizar el proceso de limpiar los recursos utilizados por el objeto de cuadro de diálogo.  
  
##  <a name="a-namesetdefaultbuttona--coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COccManager::SetDefaultButton  
 Llame a esta función para establecer el control como botón predeterminado.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene el control.  
  
 `bDefault`  
 Distinto de cero si el control debe convertirse en el botón predeterminado; en caso contrario, es cero.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control debe tener la **OLEMISC_ACTSLIKEBUTTON** conjunto de bits de estado. Para obtener más información sobre **OLEMISC** indicadores, consulte la [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) tema en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesplitdialogtemplatea--coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate  
 Llamado por el marco para dividir los controles ActiveX de los controles de cuadro de diálogo comunes.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTemplate`  
 Puntero a la plantilla de cuadro de diálogo Examinar.  
  
 `ppOleDlgItems`  
 Una lista de punteros a elementos de cuadro de diálogo son los controles ActiveX.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una estructura de plantilla de cuadro de diálogo que contiene sólo los controles ActiveX no. Si están presentes, los controles ActiveX **NULL** se devuelve.  
  
### <a name="remarks"></a>Comentarios  
 Si se encuentran los controles ActiveX, la plantilla se analiza y se crea una nueva plantilla, que contiene sólo los controles de ActiveX no. Los controles de ActiveX encontrados durante este proceso se agregan a `ppOleDlgItems`.  
  
 Si no hay ningún control de ActiveX en la plantilla, **NULL** se devuelve *.*  
  
> [!NOTE]
>  Memoria asignada para la nueva plantilla se libera en la `PostCreateDialog` (función).  
  
 Reemplazar esta función para personalizar este proceso.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [Clase COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

