---
title: CHtmlEditView (clase)
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 1254a3412846cdebd1d9accb91d27d0afbc4ef8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352079"
---
# <a name="chtmleditview-class"></a>CHtmlEditView (clase)

Proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto de la arquitectura de vista/documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Construye un objeto `CHtmlEditView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditView::Create](#create)|Crea un nuevo objeto de ventana.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Devuelve `IHTMLDocument2` la interfaz del documento actual.|
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

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView

Construye un objeto `CHtmlEditView`.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView::Create

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

*lpszClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase Windows. El nombre de clase puede ser cualquier nombre registrado con `RegisterClass` la función global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) o la función Windows. Si NULL, utiliza los atributos [CFrameWnd](../../mfc/reference/cframewnd-class.md) predeterminados predefinidos.

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana.

*dwStyle*<br/>
Especifica los atributos de estilo de ventana. De forma predeterminada, se establecen los estilos WS_VISIBLE y WS_CHILD de Windows.

*Rect*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que especifica el tamaño y la posición de la ventana. El valor *rectDefault* permite a Windows especificar el tamaño y la posición de la nueva ventana.

*pParentWnd*<br/>
Un puntero a la ventana primaria del control.

*nID*<br/>
El número de ID de la vista. De forma predeterminada, establezca AFX_IDW_PANE_FIRST.

*pContext*<br/>
Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL de forma predeterminada.

### <a name="remarks"></a>Observaciones

Este método también llamará al `Navigate` método de WebBrowser contenido para cargar un documento predeterminado (consulte [CHtmlEditView::GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument

Devuelve `IHTMLDocument2` la interfaz del documento actual.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parámetros

*ppDocument*<br/>
La interfaz [IHTMLDocument2.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView::GetStartDocument

Recupera el nombre del documento predeterminado para esta vista.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Consulte también

[Ejemplo de HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
