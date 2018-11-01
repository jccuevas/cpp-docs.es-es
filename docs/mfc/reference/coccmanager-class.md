---
title: COccManager (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 804db7be4ba796a67042e6772ae4cb631c0c232b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440188"
---
# <a name="coccmanager-class"></a>COccManager (clase)

Administra distintos sitios de control personalizado; implementado por objetos `COleControlContainer` y `COleControlSite` .

## <a name="syntax"></a>Sintaxis

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|Crea un objeto `COleContainer`.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crea los controles ActiveX, hospedados por el asociado `COleContainer` objeto.|
|[COccManager::CreateSite](#createsite)|Crea un objeto `COleClientSite`.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Recupera el código del botón predeterminado.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Determina el destino de un mensaje del cuadro de diálogo.|
|[COccManager::IsLabelControl](#islabelcontrol)|Determina si el control especificado es un control de etiqueta.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Determina si la tecla de acceso actual coincide con la tecla de acceso del control especificado.|
|[COccManager::OnEvent](#onevent)|Intentos para controlar el evento especificado.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Libera recursos asignados durante la creación del cuadro de diálogo.|
|[COccManager::PreCreateDialog](#precreatedialog)|Procesa una plantilla de cuadro de diálogo para controles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Alterna el estado predeterminado del control especificado.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Separa los controles ActiveX existentes de los controles comunes en la plantilla de cuadro de diálogo especificado.|

## <a name="remarks"></a>Comentarios

La clase base, `CNoTrackObject`, es una clase base sin documentar (ubicada en AFXTLS. (H). Diseñado para su uso por el marco de trabajo MFC, las clases derivadas de la `CNoTrackObject` clase están exentos de la detección de pérdidas de memoria. No se recomienda que derivan directamente de `CNoTrackObject`.

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

*conquistado*<br/>
Un puntero al objeto de ventana asociado al contenedor de sitios personalizados.

### <a name="return-value"></a>Valor devuelto

Un puntero para el contenedor recién creado; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre la creación de sitios personalizados, consulte [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls

Llame a esta función para crear controles de ActiveX especificados por el *pOccDialogInfo* parámetro.

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

*pWndParent*<br/>
Un puntero al elemento primario del objeto de cuadro de diálogo.

*lpszResourceName*<br/>
El nombre del recurso que se va a crear.

*pOccDialogInfo*<br/>
Un puntero a la plantilla de cuadro de diálogo usada para crear el objeto de cuadro de diálogo.

*lpResource*<br/>
Un puntero a un recurso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control se creó correctamente; en caso contrario, es cero.

##  <a name="createsite"></a>  COccManager::CreateSite

Lo llama el marco para crear un sitio del control hospedado por el contenedor al que apunta *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parámetros

*pCtrlCont*<br/>
Un puntero al contenedor del control que hospeda el sitio del control nuevo.

### <a name="return-value"></a>Valor devuelto

Un puntero al sitio del control recién creado.

### <a name="remarks"></a>Comentarios

Reemplace esta función para crear un control personalizado de sitio, mediante su [COleControlSite](../../mfc/reference/colecontrolsite-class.md)-clase derivada.

Cada contenedor de control puede hospedar varios sitios. Creación de sitios adicionales con varias llamadas a `CreateSite`.

##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode

Llame a esta función para determinar si el control es un botón de comando predeterminado.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
El objeto de ventana que contiene el control de botón.

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

- Control DLGC_DEFPUSHBUTTON es el botón predeterminado en el cuadro de diálogo.

- Control DLGC_UNDEFPUSHBUTTON no es el botón predeterminado en el cuadro de diálogo.

- **0** control no es un botón.

##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage

Lo llama el marco de trabajo para determinar si un mensaje está pensado para el cuadro de diálogo especificado y, si es así, procesa el mensaje.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*pWndDlg*<br/>
Un puntero en el cuadro de diálogo de destino previsto del mensaje.

*lpMsg*<br/>
Un puntero a un `MSG` estructura que contiene el mensaje se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado de `IsDialogMessage` consiste en comprobar los mensajes del teclado y convertirlos en selecciones para el cuadro de diálogo correspondiente. Por ejemplo, la tecla TAB, cuando se presionan, selecciona el siguiente control o grupo de controles.

Reemplace esta función para proporcionar un comportamiento personalizado para los mensajes enviados al cuadro de diálogo especificado.

##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl

Llame a esta función para determinar si el control especificado es un control de etiqueta.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Un puntero a la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control es una etiqueta; en caso contrario, cero

### <a name="remarks"></a>Comentarios

Un control label es uno que actúa como una etiqueta para cualquier control que es lo próximo en la ordenación.

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

*conquistado*<br/>
Un puntero a la ventana que contiene el control.

*lpMsg*<br/>
Un puntero al mensaje que contiene la tecla de acceso para hacer coincidir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la tecla de acceso coincide con el control; en caso contrario, cero

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

*pCmdTarget*<br/>
Un puntero a la `CCmdTarget` intentar controlar el evento de objeto

*idCtrl*<br/>
El identificador de recurso del control.

*pEvent*<br/>
Evento que se controla.

*pHandlerInfo*<br/>
Si no es NULL, `OnEvent` rellena el `pTarget` y `pmf` los miembros de la `AFX_CMDHANDLERINFO` estructura en lugar de enviar el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló el evento, en caso contrario, cero.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar el proceso de control de eventos predeterminado.

##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog

Lo llama el marco de trabajo para procesar una plantilla de cuadro de diálogo para controles ActiveX antes de crear el cuadro de diálogo real.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
Un `_AFX_OCC_DIALOG_INFO` estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados por el cuadro de diálogo.

*pOrigTemplate*<br/>
Un puntero a la plantilla de cuadro de diálogo que se usará para crear el cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Un puntero a una estructura de plantilla de cuadro de diálogo usado para crear el cuadro de diálogo.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado realiza una llamada a `SplitDialogTemplate`, determinar si hay cualquier ActiveX controla presente y, a continuación, devuelve la plantilla de cuadro de diálogo resultante.

Reemplace esta función para personalizar el proceso de creación de un cuadro de diálogo hospedar controles ActiveX.

##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog

Lo llama el marco para liberar memoria asignada para la plantilla de cuadro de diálogo.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
Un `_AFX_OCC_DIALOG_INFO` estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados por el cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Esta memoria se asignó mediante una llamada a `SplitDialogTemplate`y se utilizó para todos los controles de ActiveX hospedados en el cuadro de diálogo.

Reemplace esta función para personalizar el proceso de limpieza de los recursos utilizados por el objeto de cuadro de diálogo.

##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton

Llame a esta función para establecer el control del botón predeterminado.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Un puntero a la ventana que contiene el control.

*bNivel predeterminado*<br/>
Distinto de cero si el control deben convertirse en el botón predeterminado; en caso contrario, es cero.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El control debe tener el conjunto de bits de estado OLEMISC_ACTSLIKEBUTTON. Para obtener más información sobre marcas OLEMISC, consulte el [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) tema en el SDK de Windows.

##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate

Lo llama el marco de trabajo para dividir los controles ActiveX de los controles de cuadro de diálogo comunes.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parámetros

*pTemplate*<br/>
Un puntero a la plantilla de cuadro de diálogo que se va a examinar.

*ppOleDlgItems*<br/>
Una lista de punteros a elementos de cuadro de diálogo que son controles ActiveX.

### <a name="return-value"></a>Valor devuelto

Un puntero a una estructura de plantilla de cuadro de diálogo que contiene solo los controles ActiveX no. Si no hay controles ActiveX están presentes, se devuelve NULL.

### <a name="remarks"></a>Comentarios

Si se encuentran los controles ActiveX, se analiza la plantilla y se crea una nueva plantilla, que contiene solo los controles de ActiveX no. Los controles ActiveX encontrados durante este proceso se agregan a *ppOleDlgItems*.

Si no hay ningún control ActiveX en la plantilla, se devuelve NULL *.*

> [!NOTE]
>  Memoria asignada para la nueva plantilla se libera en la `PostCreateDialog` función.

Reemplace esta función para personalizar este proceso.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite (clase)](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer (clase)](../../mfc/reference/colecontrolcontainer-class.md)
