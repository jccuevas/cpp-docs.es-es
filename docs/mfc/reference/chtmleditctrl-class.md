---
title: CHtmlEditCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366844"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl (clase)

Proporciona la funcionalidad del control ActiveX de WebBrowser en una ventana de MFC.

## <a name="syntax"></a>Sintaxis

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Construye un objeto `CHtmlEditCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHtmlEditCtrl::Crear](#create)|Crea un control ActiveX WebBrowser y `CHtmlEditCtrl` lo adjunta al objeto. Esta función coloca automáticamente el control ActiveX WebBrowser en modo de edición.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Recupera la interfaz [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) en el documento cargado actualmente en el control WebBrowser contenido.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Recupera la dirección URL de un documento predeterminado que se va a cargar en el control WebBrowser contenido.|

## <a name="remarks"></a>Observaciones

El control WebBrowser hospedado se pone automáticamente en modo de edición después de crearlo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

Construye un objeto `CHtmlEditCtrl`.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Crear

Crea un control ActiveX WebBrowser y `CHtmlEditCtrl` lo adjunta al objeto. El control ActiveX WebBrowser navega automáticamente a un documento predeterminado y, a continuación, esta función lo coloca en modo de edición.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszWindowName*<br/>
Este parámetro no se utiliza.

*dwStyle*<br/>
Este parámetro no se utiliza.

*Rect*<br/>
Especifica el tamaño y la posición del control.

*pParentWnd*<br/>
Especifica la ventana primaria del control. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control.

*pContext*<br/>
Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument

Recupera la interfaz [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) en el documento cargado actualmente en el control WebBrowser contenido

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parámetros

*ppDocument*<br/>
La interfaz del documento.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument

Recupera la dirección URL de un documento predeterminado que se va a cargar en el control WebBrowser contenido.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
