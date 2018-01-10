---
title: Clase CHtmlEditView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs: C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98964a48be8b8c36a3d6d5bd708a51b9963ae105
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="chtmleditview-class"></a>Clase CHtmlEditView
Proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto de la arquitectura de vista/documento de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Construye un objeto `CHtmlEditView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|Crea un nuevo objeto de ventana.|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Devuelve el **IHTMLDocument2** interfaz en el documento actual.|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Recupera el nombre del documento predeterminado para esta vista.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxhtml.h  
  
##  <a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView  
 Construye un objeto `CHtmlEditView`.  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>CHtmlEditView::Create  
 Crea un nuevo objeto de ventana.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszClassName`  
 Apunta a una cadena de caracteres terminada en null que designa la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) una función global o **RegisterClass** la función de Windows. Si **NULL**, usa el valor predeterminado predefinido [CFrameWnd](../../mfc/reference/cframewnd-class.md) atributos.  
  
 `lpszWindowName`  
 Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana.  
  
 `dwStyle`  
 Especifica los atributos de estilo de ventana. De forma predeterminada, el **WS_VISIBLE** y **WS_CHILD** se establecen los estilos de Windows.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica el tamaño y la posición de la ventana. El `rectDefault` valor permite a Windows especificar el tamaño y la posición de la nueva ventana.  
  
 `pParentWnd`  
 Un puntero a la ventana primaria del control.  
  
 `nID`  
 El número de Id. de la vista. De forma predeterminada, **AFX_IDW_PANE_FIRST**.  
  
 `pContext`  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). **NULL** de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Este método también llamará el control WebBrowser independiente **Navigate** método para cargar un documento predeterminado (vea [CHtmlEditView::GetStartDocument](#getstartdocument)).  
  
##  <a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument  
 Devuelve el **IHTMLDocument2** interfaz en el documento actual.  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `ppDocument`  
 El [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interfaz.  
  
##  <a name="getstartdocument"></a>CHtmlEditView::GetStartDocument  
 Recupera el nombre del documento predeterminado para esta vista.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HTMLEdit](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)


