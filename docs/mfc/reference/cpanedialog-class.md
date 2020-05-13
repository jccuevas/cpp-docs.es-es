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
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364122"
---
# <a name="cpanedialog-class"></a>Clase CPaneDialog

La `CPaneDialog` clase admite un cuadro de diálogo no codificador y configuración acoplable.

## <a name="syntax"></a>Sintaxis

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Constructor predeterminado.|
|`CPaneDialog::~CPaneDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPaneDialog::Create](#create)|Crea un cuadro de diálogo acoplable y lo adjunta a un `CPaneDialog` objeto.|
|`CPaneDialog::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CPaneDialog::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Controla el mensaje [WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Redefine `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Controla el mensaje [de WM_ERASEBKGND.](/windows/win32/winmsg/wm-erasebkgnd) (Redefine [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Controla el mensaje [de WM_LBUTTONDBLCLK.](/windows/win32/inputdev/wm-lbuttondblclk) (Redefine [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Controla el mensaje [de WM_LBUTTONDOWN.](/windows/win32/inputdev/wm-lbuttondown) (Redefine [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Llamado por el marco de trabajo para actualizar la ventana del cuadro de diálogo. (Reemplaza [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Controla el mensaje [de WM_WINDOWPOSCHANGING.](/windows/win32/winmsg/wm-windowposchanging) (Redefine [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Especifica la plantilla de un cuadro de diálogo que es un contenedor de controles OLE.|

## <a name="remarks"></a>Observaciones

Construir `CPaneDialog` un objeto en dos pasos. En primer lugar, construya el objeto en el código. En segundo lugar, llame a [CPaneDialog::Create](#create). Debe especificar un nombre de plantilla de recurso válido o un identificador de plantilla y pasar un puntero a la ventana primaria. De lo contrario, se produce un error en el proceso de creación. El cuadro de diálogo debe especificar el estilo WS_CHILD y WS_VISIBLE. Se recomienda especificar también los estilos WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Para obtener más información, consulte [Estilos](styles-used-by-mfc.md#window-styles)de ventana .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Create

Crea un cuadro de diálogo de `CPaneDialog` acoplamiento y lo adjunta a un objeto.

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
[en] El nombre del cuadro de diálogo de acoplamiento.

*pParentWnd*<br/>
[en] Apunta a la ventana padre.

*bHasGripper*<br/>
[en] TRUE para crear el cuadro de diálogo de acoplamiento con un título (gripper); de lo contrario, FALSE.

*lpszTemplateName*<br/>
[en] El nombre de la plantilla de cuadro de diálogo de recursos.

*nStyle*<br/>
[en] El estilo de Windows.

*nID*<br/>
[en] El identificador de control.

*nIDTemplate*<br/>
[en] El identificador de recurso de la plantilla de cuadro de diálogo.

*dwTabbedStyle*<br/>
[en] El estilo de la ventana con fichas que se produce cuando el usuario arrastra otro panel de control al título de este panel de control. El valor predeterminado es AFX_CBRS_REGULAR_TABS. Para obtener más información, vea la sección Comentarios del método [CBasePane::CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

*dwControlBarStyle*<br/>
[en] Atributos de estilo adicionales. El valor predeterminado es AFX_DEFAULT_DOCKING_PANE_STYLE. Para obtener más información, vea la sección Comentarios del método [CBasePane::CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `Create` muestra `CPaneDialog` cómo utilizar el método en la clase. Este ejemplo forma parte del [ejemplo Establecer tamaño](../../overview/visual-cpp-samples.md)de panel .

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Controla el mensaje [WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog)

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*wParam*<br/>
[en] Controle el control que va a recibir el foco de teclado predeterminado.

*lParam*<br/>
[en] Especifica datos de inicialización adicionales.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE. Además, TRUE establece el foco del teclado en el control especificado por el *wParam* parámetro; FALSE impide establecer el foco de teclado predeterminado.

### <a name="remarks"></a>Observaciones

El marco de trabajo utiliza este método para inicializar los controles y la apariencia de un cuadro de diálogo. El marco de trabajo llama a este método antes de mostrar el cuadro de diálogo.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Especifica la plantilla de un cuadro de diálogo que es un contenedor de controles OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parámetros

*pOccDialogInfo*<br/>
[en] Puntero a una plantilla de cuadro de diálogo que se utiliza para crear el objeto de cuadro de diálogo. El valor de este parámetro se pasa posteriormente a la [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) método.

### <a name="return-value"></a>Valor devuelto

Siempre TRUE.

### <a name="remarks"></a>Observaciones

Este método admite la [clase COccManager,](../../mfc/reference/coccmanager-class.md) que administra los sitios de control OLE y los controles ActiveX. La estructura _AFX_OCC_DIALOG_INFO se define en el archivo de encabezado afxocc.h.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[Estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles)
