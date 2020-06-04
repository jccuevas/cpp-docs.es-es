---
title: CMultiPageDHtmlDialog (clase)
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319666"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog (clase)

Un cuadro de diálogo de varias páginas muestra varias páginas HTML secuencialmente y administra los eventos de cada página.

## <a name="syntax"></a>Sintaxis

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construye un objeto de diálogo DHTML de varias páginas (estilo asistente).|
|[CMultiPageDHtmlDialog::-CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|Destruye un objeto de cuadro de diálogo DHTML de varias páginas.|

## <a name="remarks"></a>Observaciones

El mecanismo para hacer esto es un mapa de eventos [DHTML y URL,](dhtml-event-maps.md)que contiene mapas de eventos incrustados para cada página.

## <a name="example"></a>Ejemplo

Este cuadro de diálogo de varias páginas supone tres recursos HTML que definen una funcionalidad sencilla similar a un asistente. La primera página tiene un botón **Siguiente,** la segunda un botón **Anterior** y **Siguiente,** y la tercera un botón **Anterior.** Cuando se presiona uno de los botones, una función de controlador llama a [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) para cargar la nueva página adecuada.

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

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Construye un objeto de diálogo DHTML de varias páginas (estilo asistente).

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
Cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*szHtmlResID*<br/>
Cadena terminada en null que es el nombre de un recurso HTML.

*pParentWnd*<br/>
Puntero al objeto de ventana primario o propietario (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

*nHtmlResID*<br/>
Contiene el número de identificador de un recurso HTML.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::-CMultiPageDHtmlDialog

Destruye un objeto de cuadro de diálogo DHTML de varias páginas.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Consulte también

[CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
