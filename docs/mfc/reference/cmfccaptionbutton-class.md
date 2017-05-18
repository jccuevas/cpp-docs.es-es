---
title: Clase CMFCCaptionButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCCaptionButton class
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9d6342f87622c34b671ad5ea443eb78ffd8c3838
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccaptionbutton-class"></a>Clase CMFCCaptionButton
La `CMFCCaptionButton` clase implementa un botón que se muestra en la barra de título de un panel acoplable o una ventana de marco reducido. Normalmente, el marco de trabajo crea botones de título automáticamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Construye un objeto CMFCCaptionButton.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|Devuelve el comando representado por el botón.|  
|[CMFCCaptionButton::GetIconID](#geticonid)|Devuelve el identificador de imagen asociado al botón.|  
|[CMFCCaptionButton::GetRect](#getrect)|Devuelve el rectángulo ocupado por el botón.|  
|[CMFCCaptionButton::GetSize](#getsize)|Devuelve el ancho y alto del botón.|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indica si el alto de la barra de título se establece en tamaño mini.|  
|[CMFCCaptionButton::Move](#move)|Establece la ubicación del botón draw y estado de mostrar la ventana.|  
|[CMFCCaptionButton::OnDraw](#ondraw)|Dibuja el botón de título.|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Establece el tamaño de la barra de título mini.|  
  
## <a name="remarks"></a>Comentarios  
 Puede derivar una clase de [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md) y utilice el método protegido, `AddButton`, para agregar los botones de título para una ventana de marco flotante.  
  
 CPaneFrameWnd.h define los identificadores de comando para dos tipos de botones de título:  
  
- `AFX_CAPTION_BTN_PIN`, que muestra un botón de anclaje cuando el panel de acoplamiento es compatible con el modo de ocultación automática.  
  
- `AFX_CAPTION_BTN_CLOSE`, que muestra un **cerrar** cuando el panel puede estar cerrado u oculto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCCaptionButton` de objeto y establecer el tamaño de la barra de título mini.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#43;](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton  
 Construye un objeto `CMFCCaptionButton`.  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHit`  
 Comando asociado con el botón.  
  
 [in] `bLeftAlign`  
 Especifica si el botón se alinea a la izquierda.  
  
 La tabla siguiente enumeran los valores posibles para el `nHit` parámetro.  
  
|Valor|Comando|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Botón Cerrar.|  
|`HTMINBUTTON`|Botón Minimizar.|  
|`HTMAXBUTTON`|Botón Maximizar.|  
|`AFX_HTLEFTBUTTON`|Botón de flecha izquierda.|  
|`AFX_HTRIGHTBUTTON`|Botón de flecha derecha.|  
|`AFX_HTMENU`|Botón de menú de flecha.|  
|`HTNOWHERE`|El valor predeterminado; no representa ningún comando.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de título no están asociados con un comando.  
  
 Los botones de título están alineados a la izquierda o derecha.  
  
##  <a name="gethit"></a>CMFCCaptionButton::GetHit  
 Devuelve el comando representado por el botón.  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El comando representado por el botón.  
  
 En la tabla siguiente enumera los posibles valores devueltos.  
  
|Valor|Comando|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Botón Cerrar.|  
|`HTMINBUTTON`|Botón Minimizar.|  
|`HTMAXBUTTON`|Botón Maximizar.|  
|`AFX_HTLEFTBUTTON`|Botón de flecha izquierda.|  
|`AFX_HTRIGHTBUTTON`|Botón de flecha derecha.|  
|`AFX_HTMENU`|Botón de menú de flecha.|  
|`HTNOWHERE`|El valor predeterminado; no representa ningún comando.|  
  
##  <a name="geticonid"></a>CMFCCaptionButton::GetIconID  
 Devuelve el identificador de imagen asociado al botón.  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHorz`  
 `TRUE`flecha izquierda o derecha de la imagen identificadores; `FALSE` para arriba o flecha abajo de identificadores de la imagen.  
  
 [in] `bMaximized`  
 `TRUE`un identificador de imagen maximizar; `FALSE` para un minimizar el Id. de imagen  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de la imagen.  
  
### <a name="remarks"></a>Comentarios  
 Los parámetros especifican identificadores de imagen para minimizar o maximizar los botones de título.  
  
##  <a name="getrect"></a>CMFCCaptionButton::GetRect  
 Devuelve el rectángulo ocupado por el botón.  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo que representa la ubicación del botón.  
  
### <a name="remarks"></a>Comentarios  
 Si no ve el botón, el tamaño devuelto es 0.  
  
##  <a name="getsize"></a>CMFCCaptionButton::GetSize  
 Devuelve el ancho y alto del botón.  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones externas del botón.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño devuelto incluye el borde y margen de botón.  
  
##  <a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton  
 Indica si el alto de la barra de título se establece en tamaño mini.  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el título en tamaño mini; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="move"></a>CMFCCaptionButton::Move  
 Establece la ubicación del botón draw y estado de mostrar la ventana.  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptTo`  
 La nueva ubicación.  
  
 [in] `bHide`  
 Si desea mostrar el botón.  
  
##  <a name="ondraw"></a>CMFCCaptionButton::OnDraw  
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
 [in] `pDC`  
 Puntero a un contexto de dispositivo para el botón.  
  
 [in] `bActive`  
 Si desea dibujar una imagen de botón activo.  
  
 [in] `bHorz`  
 Reservado para uso en una clase derivada.  
  
 [in] `bMaximized`  
 Si desea dibujar una imagen de botón maximizado.  
  
 [in] `bDisabled`  
 Si desea dibujar una imagen de botón activado.  
  
### <a name="remarks"></a>Comentarios  
 El `bMaximized` parámetro se utiliza cuando el botón es un maximizar o minimizar de botón.  
  
##  <a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton  
 Establece el tamaño de la barra de título mini.  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`para el alto de la barra de título mini; `FALSE` para el alto predeterminado de la barra de título.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)

