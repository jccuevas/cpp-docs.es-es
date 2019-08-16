---
title: Clase CPaneDialog
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502980"
---
# <a name="cpanedialog-class"></a>Clase CPaneDialog

La `CPaneDialog` clase admite un cuadro de diálogo no modal y acoplable.

## <a name="syntax"></a>Sintaxis

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Constructor predeterminado.|
|`CPaneDialog::~CPaneDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneDialog::Create](#create)|Crea un cuadro de diálogo acoplable y lo adjunta a un `CPaneDialog` objeto.|
|`CPaneDialog::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CPaneDialog::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Controla el mensaje [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Vuelve a definir `CBasePane::HandleInitDialog`).|
|`CPaneDialog::OnEraseBkgnd`|Controla el mensaje [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) . (Vuelve a definir [CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)).|
|`CPaneDialog::OnLButtonDblClk`|Controla el mensaje [WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) . (Vuelve a definir [CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)).|
|`CPaneDialog::OnLButtonDown`|Controla el mensaje de [WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) . (Vuelve a definir [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)).|
|`CPaneDialog::OnUpdateCmdUI`|Lo llama el marco de trabajo para actualizar la ventana de cuadro de diálogo. (Invalida [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md)).|
|`CPaneDialog::OnWindowPosChanging`|Controla el mensaje [WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) . (Vuelve a definir [CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)).|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.|

## <a name="remarks"></a>Comentarios

Construya un `CPaneDialog` objeto en dos pasos. En primer lugar, construya el objeto en el código. En segundo lugar, llame a [CPaneDialog:: Create](#create). Debe especificar un identificador de plantilla o un nombre de plantilla de recursos válido y pasar un puntero a la ventana primaria. De lo contrario, se produce un error en el proceso de creación. El cuadro de diálogo debe especificar el estilo WS_CHILD y WS_VISIBLE. Se recomienda especificar también los estilos WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Para obtener más información, consulte [estilos de ventana](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpanedialog. h

##  <a name="create"></a>  CPaneDialog::Create

Crea un cuadro de diálogo de acoplamiento y lo adjunta a un `CPaneDialog` objeto.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszWindowName*<br/>
de Nombre del cuadro de diálogo de acoplamiento.

*pParentWnd*<br/>
de Apunta a la ventana primaria.

*bHasGripper*<br/>
de TRUE para crear el cuadro de diálogo de acoplamiento con un título (agarrador); en caso contrario, FALSE.

*lpszTemplateName*<br/>
de Nombre de la plantilla de cuadro de diálogo de recursos.

*nStyle*<br/>
de Estilo de Windows.

*nID*<br/>
de IDENTIFICADOR del control.

*nIDTemplate*<br/>
de El identificador de recurso de la plantilla de cuadro de diálogo.

*dwTabbedStyle*<br/>
de Estilo de la ventana con pestañas que se produce cuando el usuario arrastra otro panel de control hasta el título de este panel de control. El valor predeterminado es AFX_CBRS_REGULAR_TABS. Para obtener más información, vea la sección Comentarios del método [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

*dwControlBarStyle*<br/>
de Atributos de estilo adicionales. El valor predeterminado es AFX_DEFAULT_DOCKING_PANE_STYLE. Para obtener más información, vea la sección Comentarios del método [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `Create` el método en `CPaneDialog` la clase. Este ejemplo forma parte del [ejemplo Set pane size](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

Controla el mensaje [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) .

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
de Identificador del control que va a recibir el foco de teclado predeterminado.

*lParam*<br/>
de Especifica datos de inicialización adicionales.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE. Además, TRUE establece el foco de teclado en el control especificado por el parámetro *wParam* ; FALSE impide establecer el foco de teclado predeterminado.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa este método para inicializar los controles y el aspecto de un cuadro de diálogo. El marco de trabajo llama a este método antes de mostrar el cuadro de diálogo.

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
de Puntero a una plantilla de cuadro de diálogo que se usa para crear el objeto de cuadro de diálogo. El valor de este parámetro se pasa posteriormente al método [COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) .

### <a name="return-value"></a>Valor devuelto

Siempre es TRUE.

### <a name="remarks"></a>Comentarios

Este método admite la clase [COccManager](../../mfc/reference/coccmanager-class.md) , que administra los sitios de control OLE y los controles ActiveX. La estructura _AFX_OCC_DIALOG_INFO se define en el archivo de encabezado afxocc. h.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)<br/>
[Estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles)
