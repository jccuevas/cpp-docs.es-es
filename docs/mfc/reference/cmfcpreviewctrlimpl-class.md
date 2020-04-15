---
title: Clase CMFCPreviewCtrlImpl
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 060e601901fa5725d7ca62f244f66784af3dc11d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375334"
---
# <a name="cmfcpreviewctrlimpl-class"></a>Clase CMFCPreviewCtrlImpl

Esta clase implementa una ventana que se coloca en una ventana host proporcionada por el Shell para vista previa enriquecida.

## <a name="syntax"></a>Sintaxis

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::-CMFCPreviewCtrlImpl](#dtor)|Destruye un objeto de control de vista previa.|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|Construye un objeto de control de vista previa.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Crear](#create)|Sobrecargado. Llamado por un controlador de vista previa enriquecida para crear la ventana de Windows.|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|Llamado por un controlador de vista previa enriquecida cuando necesita destruir este control.|
|[CMFCPreviewCtrlImpl::Focus](#focus)|Establece el foco de entrada en este control.|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|Devuelve un documento conectado a este control de vista previa.|
|[CMFCPreviewCtrlImpl::Redibujar](#redraw)|Le dice a este control que vuelva a dibujar.|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|Llamado por el controlador de vista previa para crear una relación entre la implementación del documento y el control de vista previa.|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|Establece un nuevo elemento primario para este control.|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Llamado por un controlador de vista previa enriquecida cuando necesita establecer objetos visuales de contenido de vista previa enriquecido.|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|Establece un nuevo rectángulo delimitador para este control.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|Llamado por el marco de trabajo para representar la vista previa.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|Color de fondo de la ventana de vista previa.|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|Color del texto de la ventana de vista previa.|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|Fuente utilizada para mostrar texto en la ventana de vista previa.|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|Puntero a un documento cuyo contenido se previsualiza en el control.|

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

Construye un objeto de control de vista previa.

### <a name="syntax"></a>Sintaxis

CMFCPreviewCtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFCPreviewCtrlImpl::Crear

Sobrecargado. Llamado por un controlador de vista previa enriquecida para crear la ventana de Windows.

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

*hWndParent*<br/>
Identificador de la ventana host proporcionada por el Shell para vista previa enriquecida.

*Prc*<br/>
Especifica el tamaño inicial y la posición de la ventana.

*pContext*<br/>
Puntero a un contexto de creación.

### <a name="return-value"></a>Valor devuelto

Es TRUE si la creación se realizó correctamente; en caso contrario, FALSE.

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy

Llamado por un controlador de vista previa enriquecida cuando necesita destruir este control.

### <a name="syntax"></a>Sintaxis

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint

Llamado por el marco de trabajo para representar la vista previa.

### <a name="syntax"></a>Sintaxis

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo para pintar.

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFCPreviewCtrlImpl::Focus

Establece el foco de entrada en este control.

### <a name="syntax"></a>Sintaxis

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument

Devuelve un documento conectado a este control de vista previa.

### <a name="syntax"></a>Sintaxis

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un documento, cuyo contenido se previsualiza en el control.

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor

Color de fondo de la ventana de vista previa.

### <a name="syntax"></a>Sintaxis

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor

Color de texto de la ventana de vista previa.

### <a name="syntax"></a>Sintaxis

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFCPreviewCtrlImpl::m_font fuente utilizada para mostrar texto en la ventana de vista previa.

### <a name="syntax"></a>Sintaxis

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument

Puntero a un documento cuyo contenido se previsualiza en el control.

### <a name="syntax"></a>Sintaxis

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFCPreviewCtrlImpl::Redibujar

Le dice a este control que vuelva a dibujar.

### <a name="syntax"></a>Sintaxis

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument

Llamado por el controlador de vista previa para crear una relación entre la implementación del documento y el control de vista previa.

### <a name="syntax"></a>Sintaxis

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>Parámetros

*pDocument*<br/>
Un puntero a la implementación del documento.

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost

Establece un nuevo elemento primario para este control.

### <a name="syntax"></a>Sintaxis

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la nueva ventana primaria.

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals

Llamado por un controlador de vista previa enriquecida cuando necesita establecer objetos visuales de contenido de vista previa enriquecido.

### <a name="syntax"></a>Sintaxis

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>Parámetros

*clrBack*<br/>
Color de fondo de la ventana de vista previa.

*clrText*<br/>
Color del texto de la ventana de vista previa.

*Plf*<br/>
Fuente utilizada para mostrar texto en la ventana de vista previa.

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect

Establece un nuevo rectángulo delimitador para este control.

### <a name="syntax"></a>Sintaxis

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>Parámetros

*Prc*<br/>
Especifica el nuevo tamaño y la posición del control de vista previa.

*bRedraw*<br/>
Especifica si se debe volver a dibujar el control.

### <a name="remarks"></a>Observaciones

Normalmente se establece un nuevo rectángulo delimitador cuando se cambia el tamaño del control host.

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFCPreviewCtrlImpl::-CMFCPreviewCtrlImpl

Destruye un objeto de control de vista previa.

### <a name="syntax"></a>Sintaxis

```
virtual ~CMFCPreviewCtrlImpl();
```
