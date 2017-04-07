---
title: "Macros de la aplicación auxiliar de DDX_DHtml | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- macros, exchanging data with HMTL pages
- DDX macros
- HTML pages, helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros, DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
caps.latest.revision: 14
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
ms.openlocfilehash: d3c5136b52206a1ec67e1e1fc78ec291a2954faf
ms.lasthandoff: 02/24/2017

---
# <a name="ddxdhtml-helper-macros"></a>Macros de la aplicación auxiliar de DDX_DHtml
Las macros de la aplicación auxiliar DDX_DHtml permiten un acceso sencillo a las propiedades utilizadas de controles en una página HTML.  
  
### <a name="data-exchange-macros"></a>Macros de intercambio de datos  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Establece o recupera el HTML entre las etiquetas inicial y final del elemento actual.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Establece o recupera el punto de dirección URL o delimitador de destino.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Establece o recupera la ventana o marco destino.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o un clip de vídeo en el documento.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Establece o recupera la dirección URL del marco asociado.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL del marco asociado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href
Establece o recupera el punto de dirección URL o delimitador de destino.  
  
  
  
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLANCHORELEMENT_HREF enviar Id.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target
 Establece o recupera la ventana o marco destino.  
    
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLANCHORELEMENT_TARGET enviar Id.  

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml
 Establece o recupera el HTML entre las etiquetas inicial y final del elemento actual.  
  
  
  
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLELEMENT_INNERHTML enviar Id.  
  

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLELEMENT_INNERTEXT enviar Id. 

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue  
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian. Consulte *valor* en [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).  
  
## <a name="remarks"></a>Comentarios  
 Esta macro sólo podrá realizarse cuando se ejecuta en los controles que tienen una propiedad de valor. Los controles que tienen un valor de propiedad incluyen cuadros de edición, cuadros de lista y cuadros combinados.  
  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_A_VALUE enviar Id.  

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src
Establece o recupera la dirección URL del marco asociado.  
  
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLFRAMEBASE_SRC enviar Id.  

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src
Establece o recupera la dirección URL del marco asociado.  
  
  
  
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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLFRAMEBASE_SRC enviar Id. 

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
 El valor especificado para el parámetro de identificador del control HTML.  
  
 `var`  
 El valor que se intercambian.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se usa el `DDX_DHtml_Img_Src` macro para recuperar la propiedad src de un elemento de imagen, el objeto de imagen de Internet Explorer devolverá la dirección URL completamente de escape para el origen de la imagen. Por ejemplo, si utiliza el `DDX_DHtml_Img_Src` macro para establecer la propiedad src de un elemento de imagen a la cadena "algunos interesante general", al recuperar esa propiedad, Internet Explorer devolverá la cadena "res://d:\myapplication\myapp.exe/some%20interesting%20picture."  
  
 Esta macro llama el [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) función utilizando la DISPID_IHTMLIMGELEMENT_SRC enviar Id.  

  
## <a name="see-also"></a>Vea también  
 [Clase CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

