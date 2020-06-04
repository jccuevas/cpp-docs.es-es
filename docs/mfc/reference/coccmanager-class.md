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
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360362"
---
# <a name="coccmanager-class"></a>COccManager (clase)

Administra distintos sitios de control personalizado; implementado por objetos `COleControlContainer` y `COleControlSite` .

## <a name="syntax"></a>Sintaxis

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COccManager::CreateContainer](#createcontainer)|Crea un objeto `COleContainer` .|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crea controles ActiveX, hospedados por el objeto asociado. `COleContainer`|
|[COccManager::CreateSite](#createsite)|Crea un objeto `COleClientSite` .|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Recupera el código del botón predeterminado.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Determina el destino de un mensaje de cuadro de diálogo.|
|[COccManager::IsLabelControl](#islabelcontrol)|Determina si el control especificado es un control de etiqueta.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Determina si el mnemotécnico actual coincide con el mnemotécnico del control especificado.|
|[COccManager::OnEvent](#onevent)|Intenta controlar el evento especificado.|
|[COccManager::PostCreateDialog](#postcreatedialog)|Libera los recursos asignados durante la creación del cuadro de diálogo.|
|[COccManager::PreCreateDialog](#precreatedialog)|Procesa una plantilla de cuadro de diálogo para controles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Alterna el estado predeterminado del control especificado.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Separa los controles ActiveX existentes de los controles comunes de la plantilla de cuadro de diálogo especificada.|

## <a name="remarks"></a>Observaciones

La clase `CNoTrackObject`base, , es una clase base no documentada (ubicada en AFXTLS. H). Diseñado para su uso por el marco `CNoTrackObject` de trabajo MFC, las clases derivadas de la clase están exentas de la detección de pérdida de memoria. No se recomienda que derive `CNoTrackObject`directamente de .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>COccManager::CreateContainer

Llamado por el marco de trabajo para crear un contenedor de control.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero al objeto de ventana asociado al contenedor de sitio personalizado.

### <a name="return-value"></a>Valor devuelto

Un puntero al contenedor recién creado; NULL.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre la creación de sitios personalizados, vea [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COccManager::CreateDlgControls

Llame a esta función para crear controles ActiveX especificados por el *pOccDialogInfo* parámetro.

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
Puntero al elemento primario del objeto de cuadro de diálogo.

*lpszResourceName*<br/>
El nombre del recurso que se está creando.

*pOccDialogInfo*<br/>
Puntero a la plantilla de cuadro de diálogo utilizada para crear el objeto de cuadro de diálogo.

*lpResource*<br/>
Un puntero a un recurso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control se creó correctamente; de lo contrario cero.

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>COccManager::CreateSite

Llamado por el marco de trabajo para crear un sitio de control, hospedado por el contenedor al que apunta *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parámetros

*pCtrlCont*<br/>
Puntero al contenedor de control que hospeda el nuevo sitio de control.

### <a name="return-value"></a>Valor devuelto

Un puntero al sitio de control recién creado.

### <a name="remarks"></a>Observaciones

Invalide esta función para crear un sitio de control personalizado, mediante la clase derivada [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

Cada contenedor de control puede hospedar varios sitios. Cree sitios adicionales con `CreateSite`varias llamadas a .

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Llame a esta función para determinar si el control es un botón pulsador predeterminado.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
El objeto de ventana que contiene el control de botón.

### <a name="return-value"></a>Valor devuelto

Uno de los valores siguientes:

- DLGC_DEFPUSHBUTTON Control es el botón predeterminado en el cuadro de diálogo.

- DLGC_UNDEFPUSHBUTTON Control no es el botón predeterminado en el cuadro de diálogo.

- **0** El control no es un botón.

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COccManager::IsDialogMessage

Llamado por el marco de trabajo para determinar si un mensaje está pensado para el cuadro de diálogo especificado y, si lo es, procesa el mensaje.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*pWndDlg*<br/>
Un puntero al cuadro de diálogo de destino previsto del mensaje.

*lpMsg*<br/>
Puntero a `MSG` una estructura que contiene el mensaje que se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; de lo contrario cero.

### <a name="remarks"></a>Observaciones

El comportamiento `IsDialogMessage` predeterminado de es comprobar si hay mensajes de teclado y convertirlos en selecciones para el cuadro de diálogo correspondiente. Por ejemplo, la tecla TAB, cuando se presiona, selecciona el siguiente control o grupo de controles.

Invalide esta función para proporcionar un comportamiento personalizado para los mensajes enviados al cuadro de diálogo especificado.

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COccManager::IsLabelControl

Llame a esta función para determinar si el control especificado es un control de etiqueta.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control es una etiqueta; de lo contrario cero

### <a name="remarks"></a>Observaciones

Un control de etiqueta es aquel que actúa como una etiqueta para cualquier control que sea el siguiente en el orden.

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Llame a esta función para determinar si el mnemotécnico actual coincide con el representado por el control.

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a la ventana que contiene el control.

*lpMsg*<br/>
Un puntero al mensaje que contiene el mnemotécnico para que coincida.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mnemotécnico coincide con el control; de lo contrario cero

### <a name="remarks"></a>Observaciones

## <a name="coccmanageronevent"></a><a name="onevent"></a>COccManager::OnEvent

Llamado por el marco de trabajo para controlar el evento especificado.

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parámetros

*pCmdTarget*<br/>
Un puntero `CCmdTarget` al objeto que intenta controlar el evento

*idCtrl*<br/>
El identificador de recurso del control.

*pEvent*<br/>
El evento que se está manejando.

*pHandlerInfo*<br/>
Si no `OnEvent` es NULL, `pTarget` `pmf` rellena los `AFX_CMDHANDLERINFO` miembros y de la estructura en lugar de distribuir el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló el evento, de lo contrario cero.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar el proceso de control de eventos predeterminado.

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog

Llamado por el marco de trabajo para procesar una plantilla de cuadro de diálogo para controles ActiveX antes de crear el cuadro de diálogo real.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
Estructura `_AFX_OCC_DIALOG_INFO` que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados en el cuadro de diálogo.

*pOrigTemplate*<br/>
Puntero a la plantilla de cuadro de diálogo que se utilizará para crear el cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura de plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado realiza `SplitDialogTemplate`una llamada a , determinando si hay controles ActiveX presentes y, a continuación, devuelve la plantilla de cuadro de diálogo resultante.

Reemplace esta función para personalizar el proceso de creación de un cuadro de diálogo que hospeda controles ActiveX.

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog

Llamado por el marco de trabajo para liberar memoria asignada para la plantilla de cuadro de diálogo.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
Estructura `_AFX_OCC_DIALOG_INFO` que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados en el cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Esta memoria se asignó mediante una llamada a `SplitDialogTemplate`, y se usó para los controles ActiveX hospedados en el cuadro de diálogo.

Reemplace esta función para personalizar el proceso de limpieza de los recursos utilizados por el objeto de cuadro de diálogo.

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Llame a esta función para establecer el control como el botón predeterminado.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a la ventana que contiene el control.

*bPredeterminado*<br/>
Distinto de cero si el control debe convertirse en el botón predeterminado; de lo contrario cero.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> El control debe tener el OLEMISC_ACTSLIKEBUTTON de bits de estado establecido. Para obtener más información sobre los indicadores OLEMISC, vea el tema [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

Llamado por el marco de trabajo para dividir los controles ActiveX de controles de cuadro de diálogo comunes.

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>Parámetros

*pTemplate*<br/>
Puntero a la plantilla de cuadro de diálogo que se va a examinar.

*ppOleDlgItems*<br/>
Una lista de punteros a elementos de cuadro de diálogo que son controles ActiveX.

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura de plantilla de cuadro de diálogo que contiene solo controles no ActiveX. Si no hay controles ActiveX presentes, se devuelve NULL.

### <a name="remarks"></a>Observaciones

Si se encuentra algún control ActiveX, se analiza la plantilla y se crea una nueva plantilla, que contiene solo controles no ActiveX. Los controles ActiveX encontrados durante este proceso se agregan a *ppOleDlgItems*.

Si no hay controles ActiveX en la plantilla, se devuelve NULL *.*

> [!NOTE]
> La memoria asignada para la nueva `PostCreateDialog` plantilla se libera en la función.

Invalide esta función para personalizar este proceso.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer Clase](../../mfc/reference/colecontrolcontainer-class.md)
