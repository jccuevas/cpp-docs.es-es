---
title: Clase CMFCPreviewCtrlImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPreviewCtrlImpl
- afxwin/CMFCPreviewCtrlImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCPreviewCtrlImpl class
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
caps.latest.revision: 28
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
ms.openlocfilehash: b3ccd0d6e03f652798b45ac35d36f8bc2f63e048
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpreviewctrlimpl-class"></a>Clase CMFCPreviewCtrlImpl
Esta clase implementa una ventana que se coloca en una ventana host proporcionada por el Shell para vista previa avanzada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destruye un objeto de control de vista previa.|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Construye un objeto de control de vista previa.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|Sobrecargado. Llama a un controlador de vista previa enriquecida para crear la ventana de Windows.|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Llama a un controlador de vista previa avanzada cuando es necesario destruir este control.|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|Establece el foco a este control de entrada.|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Devuelve un documento conectado a este control de vista previa.|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|Indica que este control vuelva a dibujar.|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Llamado por el controlador de vista previa para crear una relación entre la implementación de documento y el control de vista previa.|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Establece a un nuevo elemento primario para este control.|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Llama a un controlador de vista previa avanzada cuando es necesario establecer los elementos visuales de vista previa enriquecida contenido.|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Establece un nuevo rectángulo delimitador para este control.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Llamado por el marco para representar la vista previa.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Color de fondo de la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Color del texto de la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Fuente utilizada para mostrar texto en la ventana de vista previa.|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Puntero a un documento cuyo contenido se muestra una vista previa en el control.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="a-namecmfcpreviewctrlimpla-cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
Construye un objeto de control de vista previa.

### <a name="syntax"></a>Sintaxis
CMFCPreviewCtrlImpl();  

## <a name="a-namecreatea-cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Create
Sobrecargado. Llama a un controlador de vista previa enriquecida para crear la ventana de Windows.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc  
);  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc,  
   CCreateContext* pContext  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana host proporcionada por el Shell para vista previa avanzada.  
  
 `prc`  
 Especifica el tamaño inicial y la posición de la ventana.  
  
 `pContext`  
 Puntero a un contexto de creación.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la creación se realizó correctamente; de lo contrario, `FALSE`.  
  
## <a name="a-namedestroya-cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy
Llama a un controlador de vista previa avanzada cuando es necesario destruir este control.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void Destroy();  
```  
  
## <a name="a-namedopainta-cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint  
Llamado por el marco para representar la vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo para dibujar.  


## <a name="a-namefocusa-cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Focus  
Establece el foco a este control de entrada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void Focus();  
```  
## <a name="a-namegetdocumenta-cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument
Devuelve un documento conectado a este control de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un documento, cuyo contenido se muestra una vista previa en el control.

## <a name="a-namemclrbackcolora-cmfcpreviewctrlimplmclrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor  
Color de fondo de la ventana de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="a-namemclrtextcolora-cmfcpreviewctrlimplmclrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor
Color del texto de la ventana de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="a-namemfonta-cmfcpreviewctrlimplmfont--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font fuente utilizada para mostrar texto en la ventana de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
CFont m_font;  
```  
## <a name="a-namempdocumenta-cmfcpreviewctrlimplmpdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument  
Puntero a un documento cuyo contenido se muestra una vista previa en el control.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="a-nameredrawa-cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Redraw  
Indica que este control vuelva a dibujar.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void Redraw();  
```  
## <a name="a-namesetdocumenta-cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument 
Llamado por el controlador de vista previa para crear una relación entre la implementación de documento y el control de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDocument`  
 Puntero a la implementación del documento.  

## <a name="a-namesethosta-cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost  
Establece a un nuevo elemento primario para este control.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la nueva ventana primaria.  

## <a name="a-namesetpreviewvisualsa-cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals  
Llama a un controlador de vista previa avanzada cuando es necesario establecer los elementos visuales de vista previa enriquecida contenido.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `clrBack`  
 Color de fondo de la ventana de vista previa.  
  
 `clrText`  
 Color del texto de la ventana de vista previa.  
  
 `plf`  
 Fuente utilizada para mostrar texto en la ventana de vista previa. 

##  <a name="a-namesetrecta-cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect  
Establece un nuevo rectángulo delimitador para este control.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `prc`  
 Especifica el nuevo tamaño y la posición del control de vista previa.  
  
 `bRedraw`  
 Especifica si debe volver a dibujar el control.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, un nuevo rectángulo delimitador se establece cuando se cambia el tamaño del control host.  

## <a name="a-namedtora-cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destruye un objeto de control de vista previa.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  

