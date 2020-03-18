---
title: Macros auxiliares de DDX_DHtml
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
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426268"
---
# <a name="ddx_dhtml-helper-macros"></a>Macros auxiliares de DDX_DHtml

Las macros auxiliares de DDX_DHtml permiten el acceso sencillo a las propiedades de los controles que se usan habitualmente en una página HTML.

### <a name="data-exchange-macros"></a>Macros de intercambio de datos

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Establece o recupera el código HTML entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Establece o recupera la dirección URL de destino o el punto de anclaje.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Establece o recupera la ventana o el marco de destino.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o de un clip de vídeo en el documento.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Establece o recupera la dirección URL del marco asociado.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL del marco asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml. h

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Establece o recupera la dirección URL de destino o el punto de anclaje.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLANCHORELEMENT_HREF.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Establece o recupera la ventana o el marco de destino.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLANCHORELEMENT_TARGET.

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Establece o recupera el código HTML entre las etiquetas inicial y final del elemento actual.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLELEMENT_INNERHTML.

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLELEMENT_INNERTEXT.

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Establece o recupera la propiedad Value del control seleccionado.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar. Vea el *valor* en [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Observaciones

Esta macro solo se realizará correctamente cuando se ejecute en controles que tengan una propiedad Value. Los controles que tienen una propiedad de valor incluyen cuadros de edición, cuadros de lista y cuadros combinados.

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_A_VALUE.

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Establece o recupera la dirección URL del marco asociado.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Establece o recupera la dirección URL del marco asociado.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Obtiene o recupera el nombre de una imagen o de un clip de vídeo en el documento.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parámetros

*DX*<br/>
Un puntero a un objeto [CDataExchange (](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valor especificado para el parámetro de identificador del control HTML.

*var*<br/>
Valor que se va a intercambiar.

## <a name="remarks"></a>Observaciones

Cuando se usa la macro DDX_DHtml_Img_Src para recuperar la propiedad src de un elemento IMAGE, el objeto de imagen de Internet Explorer devolverá la dirección URL con escape completo para el origen de la imagen. Por ejemplo, si usa la macro DDX_DHtml_Img_Src para establecer la propiedad src de un elemento IMAGE en la cadena "alguna imagen interesante", cuando recupere esa propiedad, Internet Explorer devolverá la cadena "res: .\n\nCausa: \ la aplicación \ MyApp. exe/some %2 0 interesante %2 0".

Esta macro llama a la función [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) mediante el ID. de envío DISPID_IHTMLIMGELEMENT_SRC.

## <a name="see-also"></a>Consulte también

[CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
