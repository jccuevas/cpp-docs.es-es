---
title: Clase CPaneDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneDialog
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog::OnLButtonDblClk method
- CPaneDialog::OnLButtonDown method
- CPaneDialog::CreateObject method
- CPaneDialog::OnUpdateCmdUI method
- CPaneDialog constructor
- CPaneDialog::OnEraseBkgnd method
- CPaneDialog class
- CPaneDialog::OnWindowPosChanging method
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 27
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 85c7e338382758dd809fb770c5ab14860e362da8
ms.lasthandoff: 02/24/2017

---
# <a name="cpanedialog-class"></a>Clase CPaneDialog
La `CPaneDialog` clase es compatible con un cuadro de diálogo no modal, acoplable.  
  
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
|`CPaneDialog::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CPaneDialog::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Controla la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje. (Redefine `CBasePane::HandleInitDialog`.)|  
|`CPaneDialog::OnEraseBkgnd`|Controla la [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) mensaje. (Redefine [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|  
|`CPaneDialog::OnLButtonDblClk`|Controla la [WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) mensaje. (Redefine [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|  
|`CPaneDialog::OnLButtonDown`|Controla la [WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) mensaje. (Redefine [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|  
|`CPaneDialog::OnUpdateCmdUI`|Llamado por el marco de trabajo para actualizar la ventana de cuadro de diálogo. (Invalida [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0).)|  
|`CPaneDialog::OnWindowPosChanging`|Controla la [WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) mensaje. (Redefine [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Especifica la plantilla de un cuadro de diálogo es un contenedor de controles OLE.|  
  
## <a name="remarks"></a>Comentarios  
 Construir un `CPaneDialog` objeto en dos pasos. En primer lugar, se construye el objeto en el código. En segundo lugar, llame a [CPaneDialog::Create](#create). Debe especificar un identificador de nombre o la plantilla de la plantilla de recursos válidos y pasar un puntero a la ventana primaria. De lo contrario, se produce un error en el proceso de creación. El cuadro de diálogo debe especificar el estilo WS_CHILD y WS_VISIBLE. Se recomienda especificar los estilos WS_CLIPCHILDREN y WS_CLIPSIBLINGS. Para obtener más información, consulte [estilos de ventana](window-styles.md).  
  
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
  
##  <a name="a-namecreatea--cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Create  
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
 `TRUE`Para crear el cuadro de diálogo de acoplamiento con el título (agarrador); de lo contrario, `FALSE`.  
  
 [in] `lpszTemplateName`  
 El nombre de la plantilla de cuadro de diálogo de recursos.  
  
 [in] `nStyle`  
 El estilo de Windows.  
  
 [in] `nID`  
 El identificador del control.  
  
 [in] `nIDTemplate`  
 El identificador de recurso de la plantilla de cuadro de diálogo.  
  
 [in] `dwTabbedStyle`  
 El estilo de la ventana con fichas que se produce cuando el usuario arrastra otro panel de control en el título de este panel de control. El valor predeterminado es `AFX_CBRS_REGULAR_TABS`. Para obtener más información, vea la sección Comentarios de la [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.  
  
 [in] `dwControlBarStyle`  
 Atributos de estilo adicionales. El valor predeterminado es `AFX_DEFAULT_DOCKING_PANE_STYLE`. Para obtener más información, vea la sección Comentarios de la [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) método.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método en la `CPaneDialog` clase. Este ejemplo forma parte de la [ejemplo establece el tamaño del panel](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize&#2;](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize&3;](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="a-namehandleinitdialoga--cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog  
 Controla la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje.  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `wParam`  
 Identificador del control que va a recibir el foco de teclado predeterminado.  
  
 [in] `lParam`  
 Especifica los datos de inicialización adicionales.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; de lo contrario, `FALSE`. Además, `TRUE` establece el foco de teclado en el control especificado por la `wParam` parámetro; `FALSE` impide establecer el foco de teclado predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa este método para inicializar los controles y la apariencia de un cuadro de diálogo. El marco de trabajo llama a este método antes de mostrar el cuadro de diálogo.  
  
##  <a name="a-namesetoccdialoginfoa--cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo  
 Especifica la plantilla de un cuadro de diálogo es un contenedor de controles OLE.  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOccDialogInfo`  
 Puntero a una plantilla de cuadro de diálogo que se utiliza para crear el objeto de cuadro de diálogo. El valor de este parámetro se pasa posteriormente a la [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) método.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método admite la [COccManager](../../mfc/reference/coccmanager-class.md) (clase), que administra los sitios de control OLE y controles ActiveX. La estructura _AFX_OCC_DIALOG_INFO se define en el archivo de encabezado afxocc.h.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Estilos de ventana](../../mfc/reference/window-styles.md)




