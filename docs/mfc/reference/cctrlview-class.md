---
title: Clase de CCtrlView | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs:
- C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3503f59096d3879f986b2a8c99bdb9823ef4e24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cctrlview-class"></a>Clase de CCtrlView
Adapta la arquitectura de vista-documento a los controles comunes admitidos por las versiones 3.51 y posteriores de Windows 98 y Windows NT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|Construye un objeto `CCtrlView`.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar utilizando el contexto de dispositivo especificado.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Se llama antes de crear la ventana de Windows asociada a este objeto `CCtrlView`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contiene el estilo predeterminado de la clase de vista.|  
|[CCtrlView::m_strClass](#m_strclass)|Contiene el nombre de clase de Windows para la clase de vista.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CCtrlView` y sus derivados, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), y [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptar el arquitectura de vista-documento a los nuevos controles comunes admite Windows 95 ó 98 y Windows NT versión 3.51 y posteriores. Para obtener más información sobre la arquitectura de vista de documento, consulte [arquitectura documento/vista](../../mfc/document-view-architecture.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cctrlview"></a>  CCtrlView::CCtrlView  
 Construye un objeto `CCtrlView`.  
  
```  
CCtrlView(
    LPCTSTR lpszClass,  
    DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszClass`  
 Nombre de clase de Windows de la clase de vista.  
  
 `dwStyle`  
 Estilo de la clase de vista.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o una ventana se divide. Invalidar [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) para inicializar la vista después de que se adjunta el documento. Llame a [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) o [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) para crear el objeto de Windows.  
  
##  <a name="m_strclass"></a>  CCtrlView::m_strClass  
 Contiene el nombre de clase de Windows para la clase de vista.  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle  
 Contiene el estilo predeterminado de la clase de vista.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este estilo se aplica cuando se crea una ventana.  
  
##  <a name="ondraw"></a>  CCtrlView::OnDraw  
 Lo llama el marco para dibujar el contenido de la `CCtrlView` objeto utilizando el contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero al contexto de dispositivo en el que se produce el dibujo.  
  
### <a name="remarks"></a>Comentarios  
 `OnDraw` Normalmente, se llama para su presentación en pantalla, pasar un contexto de dispositivo de pantalla especificado por `pDC`.  
  
##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow  
 Se llama antes de crear la ventana de Windows asociada a este objeto `CWnd`.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 A [CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la creación de ventana debe continuar; 0 para indicar el error de creación.  
  
### <a name="remarks"></a>Comentarios  
 Nunca llame a esta función directamente.  
  
 La implementación predeterminada de esta función busca un **NULL** nombre de la clase de ventana y lo sustituye por un valor predeterminado adecuado. Reemplace esta función miembro para modificar la `CREATESTRUCT` antes de crea la ventana de la estructura.  
  
 Cada clase derivada de `CCtrlView` agrega su propia funcionalidad a su reemplazo de `PreCreateWindow`. De forma predeterminada, estas derivaciones de `PreCreateWindow` no están documentados. Para determinar los estilos adecuados para cada clase y las interdependencias entre los estilos, puede examinar el código fuente MFC para la clase base de la aplicación. Si elige reemplazar `PreCreateWindow`, puede determinar si los estilos utilizados en la clase base de la aplicación proporcionan la funcionalidad que necesita mediante el uso de la información recopilada desde el código fuente MFC.  
  
 Para obtener más información acerca de cómo cambiar los estilos de ventana, consulte el [cambiar los estilos de una ventana creada por MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CTreeView](../../mfc/reference/ctreeview-class.md)   
 [CListView (clase)](../../mfc/reference/clistview-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
