---
title: CCtrlView (clase) | Microsoft Docs
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
ms.openlocfilehash: fdcec255c7d2398e1bb0efa7f86a31fc5dd938e4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210208"
---
# <a name="cctrlview-class"></a>CCtrlView (clase)
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
|[CCtrlView::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar usando el contexto de dispositivo especificado.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Se llama antes de crear la ventana de Windows asociada a este objeto `CCtrlView`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contiene el estilo predeterminado para la clase de vista.|  
|[CCtrlView::m_strClass](#m_strclass)|Contiene el nombre de clase de Windows para la clase de vista.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CCtrlView` y sus derivados, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), y [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptar el arquitectura de vista-documento a los nuevos controles comunes compatible con Windows 95/98 y Windows NT versión 3.51 y versiones posteriores. Para obtener más información sobre la arquitectura de documentos y vistas, consulte [arquitectura documento/vista](../../mfc/document-view-architecture.md).  
  
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
 *lpszClass*  
 Nombre de clase de Windows de la clase de vista.  
  
 *dwStyle*  
 Estilo de la clase de vista.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o una ventana se divide. Invalidar [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) para inicializar la vista después de que se adjunta el documento. Llame a [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) o [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) para crear el objeto de Windows.  
  
##  <a name="m_strclass"></a>  CCtrlView::m_strClass  
 Contiene el nombre de clase de Windows para la clase de vista.  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle  
 Contiene el estilo predeterminado para la clase de vista.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este estilo se aplica cuando se crea una ventana.  
  
##  <a name="ondraw"></a>  CCtrlView::OnDraw  
 Lo llama el marco de trabajo para dibujar el contenido de la `CCtrlView` objeto utilizando el contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Un puntero al contexto de dispositivo en el que se produce el dibujo.  
  
### <a name="remarks"></a>Comentarios  
 `OnDraw` Normalmente se llama para presentación en pantalla, pasando un contexto de dispositivo de pantalla especificado por *pDC*.  
  
##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow  
 Se llama antes de crear la ventana de Windows asociada a este objeto `CWnd`.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 Un [CREATESTRUCT](https://msdn.microsoft.com/library/windows/desktop/ms632603) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si debe continuar la creación de la ventana; 0 para indicar el error de creación.  
  
### <a name="remarks"></a>Comentarios  
 Nunca llame a esta función directamente.  
  
 La implementación predeterminada de esta función comprueba si hay un nombre de clase de ventana NULL y se sustituye por un valor predeterminado adecuado. Reemplace esta función miembro para modificar el `CREATESTRUCT` estructura antes de crea la ventana.  
  
 Cada clase derivada de `CCtrlView` agrega su propia funcionalidad a su reemplazo de `PreCreateWindow`. Por diseño, estas derivaciones de `PreCreateWindow` no están documentados. Para determinar los estilos adecuados para cada clase y las interdependencias entre los estilos, puede examinar el código fuente MFC para la clase base de la aplicación. Si opta por reemplazar `PreCreateWindow`, puede determinar si los estilos usados en la clase base de la aplicación proporcionan la funcionalidad necesaria mediante el uso de la información recopilada desde el código fuente MFC.  
  
 Para obtener más información acerca de cómo cambiar los estilos de ventana, consulte el [cambiar los estilos de una ventana creada por MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CTreeView](../../mfc/reference/ctreeview-class.md)   
 [CListView (clase)](../../mfc/reference/clistview-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
