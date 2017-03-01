---
title: Clase de CCtrlView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCtrlView
dev_langs:
- C++
helpviewer_keywords:
- views, and common controls
- controls [MFC], common
- CCtrlView class
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: 20
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
ms.openlocfilehash: 569044de59dc3ccd73157abc86855beef57cb558
ms.lasthandoff: 02/24/2017

---
# <a name="cctrlview-class"></a>Clase de CCtrlView
Adapta la arquitectura de vista-documento a los controles comunes admitidos por las versiones 3.51 y posteriores de Windows 98 y Windows NT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|Construye un objeto `CCtrlView`.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|Llamado por el marco para dibujar usando el contexto de dispositivo especificado.|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|Se llama antes de crear la ventana de Windows asociada a este objeto `CCtrlView`.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|Contiene el estilo predeterminado de la clase de vista.|  
|[CCtrlView::m_strClass](#m_strclass)|Contiene el nombre de clase de Windows para la clase de vista.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CCtrlView` y sus derivados [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), y [CRichEditView](../../mfc/reference/cricheditview-class.md), adaptar la arquitectura de vista de documento para los nuevos controles comunes admitidos por las versiones de Windows 95 ó 98 y Windows NT 3.51 y posteriores. Para obtener más información sobre la arquitectura de vista de documento, consulte [arquitectura documento/vista](../../mfc/document-view-architecture.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecctrlviewa--cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView  
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
 El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o se divide una ventana. Invalidar [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) para inicializar la vista después de que se adjunta el documento. Llame a [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) o [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) para crear el objeto de Windows.  
  
##  <a name="a-namemstrclassa--cctrlviewmstrclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass  
 Contiene el nombre de clase de Windows para la clase de vista.  
  
```  
CString m_strClass;  
```  
  
##  <a name="a-namemdwdefaultstylea--cctrlviewmdwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle  
 Contiene el estilo predeterminado de la clase de vista.  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este estilo se aplica cuando se crea una ventana.  
  
##  <a name="a-nameondrawa--cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::OnDraw  
 Llamado por el marco para dibujar el contenido de la `CCtrlView` objeto utilizando el contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero al contexto de dispositivo en el que se produce el dibujo.  
  
### <a name="remarks"></a>Comentarios  
 `OnDraw`Normalmente, se llama para presentación en pantalla, pasando un contexto de dispositivo de pantalla especificado por `pDC`.  
  
##  <a name="a-nameprecreatewindowa--cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow  
 Se llama antes de crear la ventana de Windows asociada a este objeto `CWnd`.  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 Un [CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si debe continuar la creación de la ventana; 0 para indicar el error de creación.  
  
### <a name="remarks"></a>Comentarios  
 Nunca llame a esta función directamente.  
  
 La implementación predeterminada de esta función busca un **NULL** nombre de la clase de ventana y sustituye el valor predeterminado apropiado. Reemplace esta función miembro para modificar el `CREATESTRUCT` estructura antes de crea la ventana.  
  
 Cada clase derivada de `CCtrlView` agrega su propia funcionalidad a su reemplazo de `PreCreateWindow`. Por diseño, estas derivaciones de `PreCreateWindow` no están documentados. Para determinar los estilos adecuados para cada clase y las interdependencias entre los estilos, puede examinar el código fuente MFC para la clase base de la aplicación. Si elige reemplazar `PreCreateWindow`, puede determinar si los estilos utilizados en la clase base de la aplicación proporcionan la funcionalidad necesaria mediante el uso de la información recopilada desde el código fuente MFC.  
  
 Para obtener más información acerca de cómo cambiar los estilos de ventana, consulte el [cambiar los estilos de una ventana creada por MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CTreeView](../../mfc/reference/ctreeview-class.md)   
 [CListView (clase)](../../mfc/reference/clistview-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)

