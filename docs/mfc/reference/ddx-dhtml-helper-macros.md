---
title: Macros de la aplicación auxiliar de DDX_DHtml | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2e9d2494463b502fda85c03fa1b861e1182cfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ddxdhtml-helper-macros"></a>Macros de la aplicación auxiliar de DDX_DHtml
Las macros de la aplicación auxiliar de DDX_DHtml permiten un acceso sencillo a las propiedades utilizadas de controles en una página HTML.  
  
### <a name="data-exchange-macros"></a>Macros de intercambio de datos  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Establece o recupera el código HTML entre las etiquetas inicial y final del elemento actual.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Establece o recupera el punto de dirección URL o los delimitadores de destino.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Establece o recupera la ventana de destino o el marco.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o un clip de vídeo en el documento.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Establece o recupera la dirección URL de marco asociado.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL de marco asociado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href
Establece o recupera el punto de dirección URL o los delimitadores de destino.  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLANCHORELEMENT_HREF enviar Id.

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target
 Establece o recupera la ventana de destino o el marco.  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLANCHORELEMENT_TARGET enviar Id.  

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml
 Establece o recupera el código HTML entre las etiquetas inicial y final del elemento actual.  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLELEMENT_INNERHTML enviar Id.  
  

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText
Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLELEMENT_INNERTEXT enviar Id. 

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue  
Establece o recupera la propiedad Value del control seleccionado.  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar. Vea *valor* en [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).  
  
## <a name="remarks"></a>Comentarios  
 Esta macro sólo se realizará correctamente cuando se ejecuta en los controles que tienen una propiedad de valor. Controles que tienen una propiedad de valor incluyen cuadros de edición, cuadros de lista y cuadros combinados.  
  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_A_VALUE enviar Id.  

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src
Establece o recupera la dirección URL de marco asociado.  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLFRAMEBASE_SRC enviar Id.  

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src
Establece o recupera la dirección URL de marco asociado.  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLFRAMEBASE_SRC enviar Id. 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
Obtiene o recupera el nombre de una imagen o un clip de vídeo en el documento.  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dx`  
 Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.  
  
 `name`  
 El valor especificado para el parámetro Id. del control HTML.  
  
 `var`  
 El valor que se va a intercambiar.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se usa el `DDX_DHtml_Img_Src` macro para recuperar la propiedad src de un elemento de imagen, el objeto de imagen de Internet Explorer devolverá la dirección URL completa de escape para el origen de la imagen. Por ejemplo, si usa el `DDX_DHtml_Img_Src` macro para establecer la propiedad src de un elemento de imagen a la cadena "algunos imagen interesante", cuando se recupera esa propiedad, Internet Explorer devolverá la cadena "res://d:\myapplication\myapp.exe/some% 20interesting % 20picture."  
  
 Esta macro llama a la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función mediante el DISPID_IHTMLIMGELEMENT_SRC enviar Id.  

  
## <a name="see-also"></a>Vea también  
 [CDHtmlDialog (clase)](../../mfc/reference/cdhtmldialog-class.md)
