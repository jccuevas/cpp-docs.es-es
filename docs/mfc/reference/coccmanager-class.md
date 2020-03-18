---
title: Clase COccManager
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
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423940"
---
# <a name="coccmanager-class"></a>Clase COccManager

Administra distintos sitios de control personalizado; implementado por objetos `COleControlContainer` y `COleControlSite` .

## <a name="syntax"></a>Sintaxis

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COccManager:: CreateContainer](#createcontainer)|Crea un objeto `COleContainer`.|
|[COccManager::CreateDlgControls](#createdlgcontrols)|Crea controles ActiveX, hospedados por el objeto `COleContainer` asociado.|
|[COccManager:: CreateSite](#createsite)|Crea un objeto `COleClientSite`.|
|[COccManager::GetDefBtnCode](#getdefbtncode)|Recupera el código del botón predeterminado.|
|[COccManager::IsDialogMessage](#isdialogmessage)|Determina el destino de un mensaje de diálogo.|
|[COccManager::IsLabelControl](#islabelcontrol)|Determina si el control especificado es un control de etiqueta.|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|Determina si el mnemotécnico actual coincide con el mnemotécnico del control especificado.|
|[COccManager:: onEvent](#onevent)|Intenta controlar el evento especificado.|
|[COccManager::P ostCreateDialog](#postcreatedialog)|Libera los recursos asignados durante la creación del cuadro de diálogo.|
|[COccManager::P reCreateDialog](#precreatedialog)|Procesa una plantilla de cuadro de diálogo para controles ActiveX.|
|[COccManager::SetDefaultButton](#setdefaultbutton)|Alterna el estado predeterminado del control especificado.|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|Separa los controles ActiveX existentes de los controles comunes de la plantilla de cuadro de diálogo especificada.|

## <a name="remarks"></a>Observaciones

La clase base, `CNoTrackObject`, es una clase base no documentada (ubicada en AFXTLS. H). Diseñado para su uso en el marco de trabajo de MFC, las clases derivadas de la clase `CNoTrackObject` están exentas de la detección de pérdidas de memoria. No se recomienda derivar directamente de `CNoTrackObject`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc. h

##  <a name="createcontainer"></a>COccManager:: CreateContainer

Lo llama el marco de trabajo para crear un contenedor de controles.

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero al objeto de ventana asociado al contenedor del sitio personalizado.

### <a name="return-value"></a>Valor devuelto

Puntero al contenedor recién creado; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre la creación de sitios personalizados, vea [COleControlContainer:: AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite).

##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls

Llame a esta función para crear los controles ActiveX especificados por el parámetro *pOccDialogInfo* .

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
Nombre del recurso que se va a crear.

*pOccDialogInfo*<br/>
Un puntero a la plantilla de cuadro de diálogo que se usa para crear el objeto de cuadro de diálogo.

*lpResource*<br/>
Un puntero a un recurso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control se ha creado correctamente; de lo contrario, es cero.

##  <a name="createsite"></a>COccManager:: CreateSite

Lo llama el marco de trabajo para crear un sitio de control, hospedado por el contenedor al que apunta *pCtrlCont*.

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parámetros

*pCtrlCont*<br/>
Puntero al contenedor de controles que hospeda el nuevo sitio de control.

### <a name="return-value"></a>Valor devuelto

Puntero al sitio de control que se acaba de crear.

### <a name="remarks"></a>Observaciones

Invalide esta función para crear un sitio de control personalizado mediante la clase derivada de [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

Cada contenedor de control puede hospedar varios sitios. Cree sitios adicionales con varias llamadas a `CreateSite`.

##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode

Llame a esta función para determinar si el control es un botón de método de envío predeterminado.

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Objeto de ventana que contiene el control de botón.

### <a name="return-value"></a>Valor devuelto

Uno de los valores siguientes:

- DLGC_DEFPUSHBUTTON control es el botón predeterminado del cuadro de diálogo.

- DLGC_UNDEFPUSHBUTTON control no es el botón predeterminado del cuadro de diálogo.

- el control **0** no es un botón.

##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage

Lo llama el marco de trabajo para determinar si un mensaje está pensado para el cuadro de diálogo especificado y, si es así, procesa el mensaje.

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*pWndDlg*<br/>
Puntero al cuadro de diálogo de destino previsto del mensaje.

*lpMsg*<br/>
Puntero a una estructura de `MSG` que contiene el mensaje que se va a comprobar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; de lo contrario, es cero.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado de `IsDialogMessage` es comprobar los mensajes del teclado y convertirlos en selecciones para el cuadro de diálogo correspondiente. Por ejemplo, al presionar la tecla TAB, se selecciona el control o grupo de controles siguiente.

Invalide esta función para proporcionar un comportamiento personalizado para los mensajes enviados al cuadro de diálogo especificado.

##  <a name="islabelcontrol"></a>COccManager::IsLabelControl

Llame a esta función para determinar si el control especificado es un control de etiqueta.

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control es una etiqueta; de lo contrario, cero

### <a name="remarks"></a>Observaciones

Un control etiqueta es aquel que actúa como una etiqueta para el control que se encuentra junto a la ordenación.

##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

Llame a esta función para determinar si la tecla de método actual coincide con la que representa el control.

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
Puntero a la ventana que contiene el control.

*lpMsg*<br/>
Puntero al mensaje que contiene el mnemotécnico que debe coincidir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mnemotécnico coincide con el control; de lo contrario, cero

### <a name="remarks"></a>Observaciones

##  <a name="onevent"></a>COccManager:: onEvent

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
Puntero al objeto de `CCmdTarget` que intenta controlar el evento.

*idCtrl*<br/>
IDENTIFICADOR de recurso del control.

*As*<br/>
Evento que se está controlando.

*pHandlerInfo*<br/>
Si no es NULL, `OnEvent` rellena los miembros `pTarget` y `pmf` de la estructura `AFX_CMDHANDLERINFO` en lugar de enviar el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si se controló el evento; de lo contrario, es cero.

### <a name="remarks"></a>Observaciones

Invalide esta función para personalizar el proceso de control de eventos predeterminado.

##  <a name="precreatedialog"></a>COccManager::P reCreateDialog

Lo llama el marco de trabajo para procesar una plantilla de cuadro de diálogo para controles ActiveX antes de crear el cuadro de diálogo real.

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados por el cuadro de diálogo.

*pOrigTemplate*<br/>
Un puntero a la plantilla de cuadro de diálogo que se va a usar para crear el cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura de plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado realiza una llamada a `SplitDialogTemplate`, determinando si hay algún control ActiveX presente y, a continuación, devuelve la plantilla de cuadro de diálogo resultante.

Invalide esta función para personalizar el proceso de creación de un cuadro de diálogo que hospede controles ActiveX.

##  <a name="postcreatedialog"></a>COccManager::P ostCreateDialog

Lo llama el marco de trabajo para liberar la memoria asignada para la plantilla de cuadro de diálogo.

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` estructura que contiene información sobre la plantilla de cuadro de diálogo y los controles ActiveX hospedados por el cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Esta memoria se asignó mediante una llamada a `SplitDialogTemplate`y se utilizó para cualquier control ActiveX hospedado en el cuadro de diálogo.

Invalide esta función para personalizar el proceso de limpieza de los recursos utilizados por el objeto de cuadro de diálogo.

##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton

Llame a esta función para establecer el control como el botón predeterminado.

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene el control.

*bDefault*<br/>
Distinto de cero si el control debe convertirse en el botón predeterminado; de lo contrario, es cero.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  El control debe tener establecido el bit de estado OLEMISC_ACTSLIKEBUTTON. Para obtener más información sobre las marcas de OLEMISC, consulte el tema [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) en el Windows SDK.

##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

Lo llama el marco de trabajo para dividir los controles ActiveX de los controles de cuadro de diálogo comunes.

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

Puntero a una estructura de plantilla de cuadro de diálogo que solo contiene controles no ActiveX. Si no hay ningún control ActiveX presente, se devuelve NULL.

### <a name="remarks"></a>Observaciones

Si se encuentra algún control ActiveX, se analiza la plantilla y se crea una nueva plantilla que solo contiene controles no ActiveX. Los controles ActiveX encontrados durante este proceso se agregan a *ppOleDlgItems*.

Si no hay controles ActiveX en la plantilla, se devuelve NULL *.*

> [!NOTE]
>  La memoria asignada a la nueva plantilla se libera en la función `PostCreateDialog`.

Invalide esta función para personalizar este proceso.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite (clase)](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer (clase)](../../mfc/reference/colecontrolcontainer-class.md)
