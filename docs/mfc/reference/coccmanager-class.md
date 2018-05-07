---
title: Clase COccManager | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
dev_langs:
- C++
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b292196eb6ac8178ba43f0e66bd4814368c916fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="coccmanager-class"></a>Clase COccManager
Administra distintos sitios de control personalizado; implementado por objetos `COleControlContainer` y `COleControlSite` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
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
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Separa los controles ActiveX existentes de los controles comunes de la plantilla de cuadro de diálogo especificado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase base, **CNoTrackObject**, es una clase base sin documentar (que se encuentra en AFXTLS. (H). Diseñado para su uso por el marco de trabajo MFC, las clases derivadas de la **CNoTrackObject** clase están exentos de la detección de pérdidas de memoria. No se recomienda derivar directamente de **CNoTrackObject**.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 Lo llama el marco para crear un contenedor de control.  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero al objeto de ventana asociado al contenedor de sitio personalizado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contenedor recién creado; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la creación de sitios personalizados, vea [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
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
 El nombre del recurso que se está creando.  
  
 `pOccDialogInfo`  
 Un puntero a la plantilla de cuadro de diálogo usada para crear el objeto de cuadro de diálogo.  
  
 `lpResource`  
 Un puntero a un recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control se creó correctamente; cero en caso contrario.  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 Lo llama el marco para crear un sitio de control, hospedado por el contenedor que señala `pCtrlCont`.  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCtrlCont`  
 Un puntero al contenedor del control que hospeda el sitio del control nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio del control recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para crear un control personalizado de sitio, con su [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-clase derivada.  
  
 Cada contenedor de control puede hospedar varios sitios. Crear sitios adicionales en varias llamadas a `CreateSite`.  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
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
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 Lo llama el marco de trabajo para determinar si un mensaje está diseñado para el cuadro de diálogo especificado y, si es así, procesa el mensaje.  
  
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
 Es distinto de cero si se procesa el mensaje; cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado de `IsDialogMessage` consiste en comprobar si hay mensajes de teclado y convertirlos en selecciones para el cuadro de diálogo correspondiente. Por ejemplo, la tecla TAB, cuando se presionan, selecciona el siguiente control o grupo de controles.  
  
 Reemplace esta función para proporcionar un comportamiento personalizado para los mensajes enviados al cuadro de diálogo especificado.  
  
##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl  
 Llame a esta función para determinar si el control especificado es un control de etiqueta.  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero a la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control es una etiqueta; en caso contrario cero  
  
### <a name="remarks"></a>Comentarios  
 Un control label es aquel que actúa como una etiqueta para cualquier control que es el siguiente en la ordenación.  
  
##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic  
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
 Un puntero a la ventana que contiene el control.  
  
 `lpMsg`  
 Un puntero al mensaje que contiene la tecla de acceso debe coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la tecla de acceso coincide con el control; en caso contrario cero  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onevent"></a>  COccManager::OnEvent  
 Lo llama el marco de trabajo para controlar el evento especificado.  
  
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
 Si no **NULL**, `OnEvent` rellena la **pTarget** y **pmf** los miembros de la **AFX_CMDHANDLERINFO** en lugar de la estructura enviar el comando. Normalmente, este parámetro debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el evento, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para personalizar el proceso de control de eventos de forma predeterminada.  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 Lo llama el marco de trabajo para procesar una plantilla de cuadro de diálogo para controles ActiveX antes de crear el cuadro de diálogo real.  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles de ActiveX alojados en el cuadro de diálogo.  
  
 *pOrigTemplate*  
 Un puntero a la plantilla de cuadro de diálogo que se usará para crear el cuadro de diálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una estructura de plantilla de cuadro de diálogo utilizado para crear el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado realiza una llamada a `SplitDialogTemplate`, determinar si hay cualquier ActiveX controla presente y, a continuación, devuelve la plantilla de cuadro de diálogo resultante.  
  
 Reemplace esta función para personalizar el proceso de creación de un cuadro de diálogo hospedar controles ActiveX.  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 Lo llama el marco para liberar memoria asignada para la plantilla de cuadro de diálogo.  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOccDialogInfo`  
 Un **_AFX_OCC_DIALOG_INFO** estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles de ActiveX alojados en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Esta memoria se asignó mediante una llamada a `SplitDialogTemplate`y se usó para todos los controles ActiveX hospedados en el cuadro de diálogo.  
  
 Reemplace esta función para personalizar el proceso de limpiar los recursos utilizados por el objeto de cuadro de diálogo.  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 Llame a esta función para establecer el control como el botón predeterminado.  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero a la ventana que contiene el control.  
  
 `bDefault`  
 Es distinto de cero si el control debe convertirse en el botón predeterminado; cero en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control debe tener la **OLEMISC_ACTSLIKEBUTTON** conjunto de bits de estado. Para obtener más información sobre **OLEMISC** marcas, consulte el [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) tema en el SDK de Windows.  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 Lo llama el marco para dividir los controles ActiveX de los controles de cuadro de diálogo comunes.  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTemplate`  
 Un puntero a la plantilla de cuadro de diálogo para examinar.  
  
 `ppOleDlgItems`  
 Una lista de punteros a elementos de cuadro de diálogo que son controles de ActiveX.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una estructura de plantilla de cuadro de diálogo que contiene solo los controles de ActiveX no. Si no hay controles ActiveX están presentes, **NULL** se devuelve.  
  
### <a name="remarks"></a>Comentarios  
 Si se encuentran los controles ActiveX, se analiza la plantilla y se crea una nueva plantilla, que contiene solo los controles de ActiveX no. Los controles de ActiveX encontrados durante este proceso se agregan a `ppOleDlgItems`.  
  
 Si no hay ningún control ActiveX en la plantilla, **NULL** se devuelve *.*  
  
> [!NOTE]
>  Memoria asignada para la nueva plantilla se libera en la `PostCreateDialog` (función).  
  
 Reemplace esta función para personalizar este proceso.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase COleControlSite](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer (clase)](../../mfc/reference/colecontrolcontainer-class.md)
