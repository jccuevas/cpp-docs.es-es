---
title: Clase CPaneDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36f620f0a29e7d1715e7cb5bfb83c0685f97f643
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cpanedialog-class"></a>Clase CPaneDialog
La `CPaneDialog` clase es compatible con un cuadro de diálogo no modal, acoplable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|Constructor predeterminado.|  
|`CPaneDialog::~CPaneDialog`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|Crea un cuadro de diálogo acoplable y lo adjunta a un `CPaneDialog` objeto.|  
|`CPaneDialog::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CPaneDialog::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Controla la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje. (Redefine `CBasePane::HandleInitDialog`.)|  
|`CPaneDialog::OnEraseBkgnd`|Controla la [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) mensaje. (Redefine [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|  
|`CPaneDialog::OnLButtonDblClk`|Controla la [WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) mensaje. (Redefine [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|  
|`CPaneDialog::OnLButtonDown`|Controla la [WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) mensaje. (Redefine [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|  
|`CPaneDialog::OnUpdateCmdUI`|Lo llama el marco de trabajo para actualizar la ventana de cuadro de diálogo. (Invalida [CDockablePane:: OnUpdateCmdUI](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0).)|  
|`CPaneDialog::OnWindowPosChanging`|Controla la [WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) mensaje. (Redefine [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.|  
  
## <a name="remarks"></a>Comentarios  
 Construir un `CPaneDialog` objeto en dos pasos. En primer lugar, construya el objeto en el código. En segundo lugar, llame a [CPaneDialog::Create](#create). Debe especificar un identificador de nombre o la plantilla de la plantilla de recurso válido y pasar un puntero a la ventana primaria. En caso contrario, se produce un error en el proceso de creación. El cuadro de diálogo debe especificar el estilo WS_CHILD y WS_VISIBLE. Se recomienda que también especifique los estilos WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Para obtener más información, consulte [estilos de ventana](styles-used-by-mfc.md#window-styles).  
  
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
 [in] `lpszWindowName`  
 El nombre del cuadro de diálogo de acoplamiento.  
  
 [in] `pParentWnd`  
 Apunta a la ventana primaria.  
  
 [in] `bHasGripper`  
 `TRUE` Para crear el cuadro de diálogo de acoplamiento con un título (barra de redimensionamiento); en caso contrario, `FALSE`.  
  
 [in] `lpszTemplateName`  
 El nombre de la plantilla de cuadro de diálogo de recursos.  
  
 [in] `nStyle`  
 El estilo de Windows.  
  
 [in] `nID`  
 El identificador del control.  
  
 [in] `nIDTemplate`  
 El identificador de recurso de la plantilla de cuadro de diálogo.  
  
 [in] `dwTabbedStyle`  
 El estilo de la ventana con pestañas que se produce cuando el usuario arrastra otro panel de control en el título de este panel de control. El valor predeterminado es `AFX_CBRS_REGULAR_TABS`. Para obtener más información, vea la sección Comentarios de la [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.  
  
 [in] `dwControlBarStyle`  
 Atributos de estilo adicionales. El valor predeterminado es `AFX_DEFAULT_DOCKING_PANE_STYLE`. Para obtener más información, vea la sección Comentarios de la [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método en la `CPaneDialog` clase. Este ejemplo forma parte de la [ejemplo establece el tamaño del panel](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog  
 Controla la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje.  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `wParam`  
 Identificador del control que va a recibir el foco del teclado predeterminado.  
  
 [in] `lParam`  
 Especifica los datos de inicialización adicionales.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si este método se realiza correctamente; en caso contrario, `FALSE`. Además, `TRUE` establece el foco del teclado al control especificado por el `wParam` parámetro; `FALSE` impide establecer el foco de teclado predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa este método para inicializar la apariencia de un cuadro de diálogo y los controles. El marco de trabajo llama a este método antes de mostrar el cuadro de diálogo.  
  
##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo  
 Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles OLE.  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOccDialogInfo`  
 Puntero a una plantilla de cuadro de diálogo que se utiliza para crear el objeto de cuadro de diálogo. El valor de este parámetro se pasa posteriormente en el [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) método.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método es compatible con la [COccManager](../../mfc/reference/coccmanager-class.md) (clase), que administra sitios de control OLE y controles ActiveX. La estructura _AFX_OCC_DIALOG_INFO se define en el archivo de encabezado afxocc.h.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles)



