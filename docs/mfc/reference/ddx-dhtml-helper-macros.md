---
title: DDX_DHtml auxiliar Macros
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: e2deed5e3fb63f46d83cf4c6f0d3c13525e93a2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592544"
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml auxiliar Macros

Las macros de la aplicación auxiliar DDX_DHtml permiten un acceso sencillo a las propiedades utilizadas de controles en una página HTML.

### <a name="data-exchange-macros"></a>Macros de intercambio de datos

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Establece o recupera el HTML entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Establece o recupera el punto de dirección URL o delimitador de destino.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Establece o recupera la ventana de destino o el marco.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o un clip de vídeo en el documento.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Establece o recupera la dirección URL del marco asociado.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL del marco asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Establece o recupera el punto de dirección URL o delimitador de destino.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLANCHORELEMENT_HREF el identificador de envío

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target

Establece o recupera la ventana de destino o el marco.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLANCHORELEMENT_TARGET el identificador de envío

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml

Establece o recupera el HTML entre las etiquetas inicial y final del elemento actual.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLELEMENT_INNERHTML el identificador de envío

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText

Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLELEMENT_INNERTEXT el identificador de envío

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Establece o recupera la propiedad Value del control seleccionado.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian. Consulte *valor* en [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Comentarios

Esta macro solo surtirán efecto cuando se ejecuta en los controles que tienen una propiedad de valor. Los controles que tienen una propiedad de valor incluyen los cuadros combinados, cuadros de lista y cuadros de edición.

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_A_VALUE el identificador de envío

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Establece o recupera la dirección URL del marco asociado.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLFRAMEBASE_SRC el identificador de envío

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Establece o recupera la dirección URL del marco asociado.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLFRAMEBASE_SRC el identificador de envío

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Obtiene o recupera el nombre de una imagen o un clip de vídeo en el documento.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*name*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*var*<br/>
El valor que se intercambian.

## <a name="remarks"></a>Comentarios

Al utilizar la macro DDX_DHtml_Img_Src para recuperar la propiedad src de un elemento de imagen, el objeto de imagen de Internet Explorer devolverá la dirección URL por completo con escape para el origen de imagen. Por ejemplo, si usa la macro DDX_DHtml_Img_Src para establecer la propiedad src de un elemento de imagen a la cadena "algunos interesante imagen", al recuperar esa propiedad, Internet Explorer devolverá la cadena "res://d:\myapplication\myapp.exe/some% 20interesting % 20picture."

Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLIMGELEMENT_SRC el identificador de envío

## <a name="see-also"></a>Vea también

[CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
