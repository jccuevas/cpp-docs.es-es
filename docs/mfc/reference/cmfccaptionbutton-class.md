---
title: Clase CMFCCaptionButton | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df36f8a6af5d8ad7e2a96780e02f236e3225333d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040634"
---
# <a name="cmfccaptionbutton-class"></a>Clase CMFCCaptionButton
La `CMFCCaptionButton` clase implementa un botón que se muestra en la barra de título de un panel acoplable o una ventana de marco reducido. Normalmente, el marco de trabajo crea botones de título automáticamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Construye un objeto CMFCCaptionButton.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|Devuelve el comando representado por el botón.|  
|[CMFCCaptionButton::GetIconID](#geticonid)|Devuelve el Id. de imagen asociado con el botón.|  
|[CMFCCaptionButton::GetRect](#getrect)|Devuelve el rectángulo ocupado por el botón.|  
|[CMFCCaptionButton::GetSize](#getsize)|Devuelve el ancho y alto del botón.|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indica si el alto de la barra de título se establece en tamaño mini.|  
|[CMFCCaptionButton::Move](#move)|Establece la ubicación del botón draw y estado de mostrar la ventana.|  
|[CMFCCaptionButton::OnDraw](#ondraw)|Dibuja el botón de título.|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Establece el tamaño mini de la barra de título.|  
  
## <a name="remarks"></a>Comentarios  
 Puede derivar una clase de [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md) y utilice el método protegido, `AddButton`, para agregar botones de título para una ventana de marco flotante.  
  
 CPaneFrameWnd.h define los identificadores de comando para dos tipos de botones de título:  
  
- `AFX_CAPTION_BTN_PIN`, que muestra un botón de anclaje cuando el panel de acoplamiento es compatible con el modo de ocultación automática.  
  
- `AFX_CAPTION_BTN_CLOSE`, que muestra un **cerrar** botón cuando el panel puede estar cerrado u oculto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCCaptionButton` de objeto y establecer el tamaño mini de la barra de título.  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton  
 Construye un objeto `CMFCCaptionButton`.  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nHit*  
 El comando asociado con el botón.  
  
 [in] *bLeftAlign*  
 Especifica si el botón se alinea a la izquierda.  
  
 En la tabla siguiente se enumera los valores posibles para la *nHit* parámetro.  
  
|Valor|Comando|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Botón Cerrar.|  
|`HTMINBUTTON`|Botón de minimizar.|  
|`HTMAXBUTTON`|Botón de maximizar.|  
|`AFX_HTLEFTBUTTON`|Botón de flecha izquierda.|  
|`AFX_HTRIGHTBUTTON`|Botón de flecha derecha.|  
|`AFX_HTMENU`|Abajo botón de menú de flecha.|  
|`HTNOWHERE`|El valor predeterminado; no representa ningún comando.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de título no están asociados con un comando.  
  
 Botones de título se alinean a la izquierda o derecha.  
  
##  <a name="gethit"></a>  CMFCCaptionButton::GetHit  
 Devuelve el comando representado por el botón.  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El comando representado por el botón.  
  
 En la siguiente tabla muestra los valores devueltos posibles.  
  
|Valor|Comando|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Botón Cerrar.|  
|`HTMINBUTTON`|Botón de minimizar.|  
|`HTMAXBUTTON`|Botón de maximizar.|  
|`AFX_HTLEFTBUTTON`|Botón de flecha izquierda.|  
|`AFX_HTRIGHTBUTTON`|Botón de flecha derecha.|  
|`AFX_HTMENU`|Abajo botón de menú de flecha.|  
|`HTNOWHERE`|El valor predeterminado; no representa ningún comando.|  
  
##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID  
 Devuelve el Id. de imagen asociado con el botón.  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHorz*  
 `TRUE` flecha izquierda o derecha de la imagen identificadores; `FALSE` para hacia arriba o flecha abajo de identificadores de la imagen.  
  
 [in] *bMaximized*  
 `TRUE` para un identificador de imagen maximizar; `FALSE` para un minimizar la imagen identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de la imagen.  
  
### <a name="remarks"></a>Comentarios  
 Los parámetros especifican identificadores de imagen para minimizar o maximizar botones de título.  
  
##  <a name="getrect"></a>  CMFCCaptionButton::GetRect  
 Devuelve el rectángulo ocupado por el botón.  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo que representa la ubicación del botón.  
  
### <a name="remarks"></a>Comentarios  
 Si no ve el botón, el tamaño devuelto es 0.  
  
##  <a name="getsize"></a>  CMFCCaptionButton::GetSize  
 Devuelve el ancho y alto del botón.  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones externas del botón.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño devuelto incluye el borde y el margen de botón.  
  
##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton  
 Indica si el alto de la barra de título se establece en tamaño mini.  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el título se establece en tamaño mini; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="move"></a>  CMFCCaptionButton::Move  
 Establece la ubicación del botón draw y estado de mostrar la ventana.  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *ptTo*  
 La nueva ubicación.  
  
 [in] *bHide*  
 Si se debe mostrar el botón.  
  
##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw  
 Dibuja el botón de título.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo para el botón.  
  
 [in] *bSecuencias de ActiveX*  
 Si se debe dibujar una imagen de botón activo.  
  
 [in] *bHorz*  
 Reservado para uso en una clase derivada.  
  
 [in] *bMaximized*  
 Si se debe dibujar una imagen del botón maximizada.  
  
 [in] *bDeshabilitado*  
 Si se debe dibujar una imagen del botón habilitado.  
  
### <a name="remarks"></a>Comentarios  
 El *bMaximized* parámetro se utiliza cuando el botón es un maximizar o minimizar botón.  
  
##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton  
 Establece el tamaño mini de la barra de título.  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bSet*  
 `TRUE` para el alto de la barra de título mini; `FALSE` para el alto predeterminado de la barra de título.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
