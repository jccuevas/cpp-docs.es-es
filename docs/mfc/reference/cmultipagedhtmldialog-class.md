---
title: CMultiPageDHtmlDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 66ab996a810c7409d689d600758828130d4237f1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283753"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog (clase)

Un cuadro de diálogo de varias páginas muestra varias páginas HTML secuencialmente y administra los eventos de cada página.

## <a name="syntax"></a>Sintaxis

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construye un objeto de cuadro de diálogo de varias páginas (Asistente de estilo) DHTML.|
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Destruye un objeto de cuadro de diálogo DHTML varias páginas.|

## <a name="remarks"></a>Comentarios

El mecanismo para hacerlo es un [mapa de eventos DHTML y la dirección URL](dhtml-event-maps.md), que contiene incrustado mapas de eventos para cada página.

## <a name="example"></a>Ejemplo

Este cuadro de diálogo de varias páginas se da por supuesto tres recursos HTML que definen la funcionalidad de asistente simple. La primera página tiene un **siguiente** button, el segundo un **Prev** y **siguiente** botón y el tercero un **Prev** botón. Cuando se presiona uno de los botones, llama una función de controlador [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) para cargar la nueva página adecuada.

Las partes pertinentes de la declaración de clase (en CMyMultiPageDlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Las partes pertinentes de la implementación de la clase (en CMyMultipageDlg.cpp):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Construye un objeto de cuadro de diálogo de varias páginas (Asistente de estilo) DHTML.

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
La cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*szHtmlResID*<br/>
La cadena terminada en null que es el nombre de un recurso HTML.

*pParentWnd*<br/>
Un puntero al objeto de ventana principal o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de Id. de un recurso de plantilla de cuadro de diálogo.

*nHtmlResID*<br/>
Contiene el número de Id. de un recurso HTML.

##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog

Destruye un objeto de cuadro de diálogo DHTML varias páginas.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Vea también

[CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
