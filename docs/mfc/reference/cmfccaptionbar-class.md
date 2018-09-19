---
title: CMFCCaptionBar (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5131479af7f34f1cc43cf91adfd0bd3ac52a594b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722987"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar (clase)
Un `CMFCCaptionBar` objeto es una barra de controles que puede mostrar tres elementos: un botón, una etiqueta de texto y un mapa de bits. Puede mostrar un solo elemento de cada tipo al mismo tiempo. Puede alinear cada elemento al borde izquierdo o derecho del control o al centro. También puede aplicar un estilo plano o 3D a los bordes superior e inferior de la barra de título.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|Crea el control de barra de título y la conecta a la `CMFCCaptionBar` objeto.|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Indica si se puede insertar otro panel dinámicamente entre la barra de título y su marco primario. (Invalida [cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|Habilita o deshabilita el botón en la barra de título.|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|Devuelve la alineación del elemento especificado.|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Devuelve el tamaño del borde de la barra de título.|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Recupera el rectángulo delimitador del botón en la barra de título.|  
|[CMFCCaptionBar::GetMargin](#getmargin)|Devuelve la distancia entre el borde de los elementos de la barra de título y el borde del control de barra de título.|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Especifica si la barra de título está en el modo de barra de mensajes.|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Quita la imagen de mapa de bits de la barra de título.|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|Quita el botón de la barra de título.|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Quita el icono de la barra de título.|  
|[CMFCCaptionBar::RemoveText](#removetext)|Quita la etiqueta de texto de la barra de título.|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Establece la imagen de mapa de bits de la barra de título.|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Establece el tamaño del borde de la barra de título.|  
|[CMFCCaptionBar::SetButton](#setbutton)|Establece el botón de la barra de título.|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Especifica si se mantiene presionado el botón.|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Establece la información sobre herramientas para el botón.|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Establece el estilo de borde de la barra de título.|  
|[CMFCCaptionBar::SetIcon](#seticon)|Establece el icono para una barra de título.|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Establece la información sobre herramientas de la imagen de la barra de título.|  
|[CMFCCaptionBar::SetMargin](#setmargin)|Establece la distancia entre el borde del elemento de barra de título y el borde del control de barra de título.|  
|[CMFCCaptionBar::SetText](#settext)|Establece la etiqueta de texto de la barra de título.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Lo llama el marco de trabajo para rellenar el fondo de la barra de título.|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Lo llama el marco de trabajo para dibujar el borde de la barra de título.|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Lo llama el marco de trabajo para dibujar el botón de barra de título.|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Lo llama el marco de trabajo para dibujar la imagen de la barra de título.|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Lo llama el marco de trabajo para dibujar el texto de la barra de título.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|El color de fondo de la barra de título.|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|El color del borde de la barra de título.|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Color del texto de la barra de título.|  
  
## <a name="remarks"></a>Comentarios  
 Para crear una barra de título, siga estos pasos:  
  
1.  Construir la `CMFCCaptionBar` objeto. Normalmente, agregaría la barra de título para una clase de ventana de marco.  
  
2.  Llame a la [CMFCCaptionBar::Create](#create) método para crear el control de barra de título y adjuntarlo a la `CMFCCaptionBar` objeto.  
  
3.  Llame a [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), y [CMFCCaptionBar::SetBitmap](#setbitmap)para establecer los elementos de la barra de título.  
  
 Cuando se establece el elemento de botón, debe asignar un identificador de comando para el botón. Cuando el usuario hace clic en el botón, la barra de título enruta los mensajes WM_COMMAND que tienen este identificador a la ventana de marco principal.  
  
 La barra de título también puede trabajar en modo de barra de mensajes, que emula la barra de mensajes que aparece en las aplicaciones de Microsoft Office 2007. En el modo de barra de mensajes, la barra de título muestra un mapa de bits, un mensaje y un botón (que normalmente se abre un cuadro de diálogo.) Puede asignar una información sobre herramientas del mapa de bits.  
  
 Para habilitar el modo de barra de mensajes, llame a [CMFCCaptionBar::Create](#create) y establezca el cuarto parámetro (bIsMessageBarMode) en TRUE.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCCaptionBar` clase. El ejemplo muestra cómo crear el control de barra de título, establezca un borde 3D de la barra de título, Establece la distancia, en píxeles, entre el borde del título de la barra elementos y el borde del control de barra de título, establezca el botón de la barra de título , Establece la información sobre herramientas para el botón, establezca la etiqueta de texto de la barra de título, Establece la imagen de mapa de bits de la barra de título y establecer la información sobre herramientas para la imagen en la barra de título. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcaptionbar.h  
  
##  <a name="create"></a>  CMFCCaptionBar::Create  
 Crea el control de barra de título y la conecta a la `CMFCCaptionBar` objeto.  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwStyle*  
 La combinación de OR lógica de los estilos de barra de título.  
  
 *pParentWnd*  
 La ventana primaria del control de barra de título.  
  
 *uID*  
 El identificador de control de barra de título.  
  
 *nHeight*  
 El alto, en píxeles, del control de barra de título. Si es -1, el alto se calcula según el alto del icono, el texto y el botón que muestra el control de barra de título.  
  
 *bIsMessageBarMode*  
 TRUE si la barra de título está en el modo de barra de mensajes; FALSE en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el control de barra de título se ha creado correctamente; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CMFCCaptionBar` objeto en dos pasos. En primer lugar llame al constructor y, a continuación, se llama a la `Create` método, que crea el control de Windows y lo adjunta a la `CMFCCaptionBar` objeto.  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore  
 Indica si se puede insertar otro panel dinámicamente entre la barra de título y su marco primario.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A menos que se reemplaza, devuelve FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton  
 Habilita o deshabilita el botón en la barra de título.  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
*bHabilitar el*<br/>
[in] TRUE para habilitar el botón, es FALSE para deshabilitar el botón.  
  
##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment  
 Devuelve la alineación del elemento especificado.  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>Parámetros  
*Elem*<br/>
[in] Un elemento de la barra de título para el que se va a recuperar la alineación.  
  
### <a name="return-value"></a>Valor devuelto  
 La alineación de un elemento, como un botón, un mapa de bits, texto o un icono.  
  
### <a name="remarks"></a>Comentarios  
 La alineación del elemento puede ser uno de los siguientes valores:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize  
 Devuelve el tamaño del borde de la barra de título.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño, en píxeles, del borde.  
  
##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect  
 Recupera el rectángulo delimitador del botón en la barra de título.  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` objeto que contiene las coordenadas del rectángulo del botón en la barra de título.  
  
##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin  
 Devuelve la distancia entre el borde de los elementos de la barra de título y el borde del control de barra de título.  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de barra de título.  
  
##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode  
 Especifica si la barra de título está en el modo de barra de mensajes.  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la barra de título está en el modo de barra de mensajes; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de barra de mensajes, la barra de título muestra una imagen con una información sobre herramientas, un mensaje de texto y un botón.  
  
##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground  
 El color de fondo de la barra de título.  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder  
 El color del borde de la barra de título.  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText  
 Color del texto de la barra de título.  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground  
 Lo llama el marco de trabajo para rellenar el fondo de la barra de título.  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero al contexto de dispositivo de la barra de título.  
  
*Rect*<br/>
[in] El rectángulo delimitador para rellenar.  
  
### <a name="remarks"></a>Comentarios  
 El `OnDrawBackground` método se llama cuando es rellenar el fondo de la barra de título. La implementación predeterminada rellena el fondo mediante el uso de la [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) color.  
  
 Invalide este método en un `CMFCCaptionBar` clase derivada para personalizar la apariencia de la barra de título.  
  
##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder  
 Lo llama el marco de trabajo para dibujar el borde de la barra de título.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un contexto de dispositivo que se usa para mostrar los bordes.  
  
*Rect*<br/>
[in] El rectángulo delimitador.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los bordes tienen el estilo plano.  
  
 Invalide este método en un `CMFCCaptionBar` clase derivada para personalizar la apariencia de los bordes de la barra de título.  
  
##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton  
 Lo llama el marco de trabajo para dibujar el botón de barra de título.  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo que se usa para mostrar el botón.  
  
*Rect*<br/>
[in] El rectángulo delimitador del botón.  
  
*strButton*<br/>
[in] Etiqueta de texto del botón.  
  
*bHabilitado*<br/>
[in] TRUE si el botón está habilitado; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un `CMFCCaptionBar` clase derivada para personalizar la apariencia del botón de la barra de título.  
  
##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage  
 Lo llama el marco de trabajo para dibujar la imagen de la barra de título.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo que se usa para mostrar la imagen.  
  
*Rect*<br/>
[in] Especifica el rectángulo delimitador de la imagen.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un `CMFCCaptionBar` clase derivada para personalizar la apariencia de la imagen.  
  
##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText  
 Lo llama el marco de trabajo para dibujar el texto de la barra de título.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo que se usa para mostrar el botón.  
  
*Rect*<br/>
[in] El rectángulo delimitador del texto.  
  
*strText*<br/>
[in] La cadena de texto para mostrar.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada muestra el texto mediante el uso de `CDC::DrawText` y [CMFCCaptionBar::m_clrBarText](#m_clrbartext) color.  
  
 Invalide este método en un `CMFCCaptionBar` clase derivada para personalizar la apariencia del texto de la barra de título.  
  
##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap  
 Quita la imagen de mapa de bits de la barra de título.  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton  
 Quita el botón de la barra de título.  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>Comentarios  
 El diseño de elementos de la barra de título se ajustan automáticamente.  
  
##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon  
 Quita el icono de la barra de título.  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText  
 Quita la etiqueta de texto de la barra de título.  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap  
 Establece la imagen de mapa de bits de la barra de título.  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parámetros  
*hBitmap*<br/>
[in] El identificador del mapa de bits para establecer.  
  
*clrTransparent*<br/>
[in] Un valor RGB que especifica el color transparente del mapa de bits.  
  
*bStretch*<br/>
[in] Si es TRUE, se ajusta el mapa de bits si no se ajusta a la imagen del rectángulo delimitador. En caso contrario, no se ajusta el mapa de bits.  
  
*bmpAlignment*<br/>
[in] La alineación del mapa de bits.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer un mapa de bits en una barra de título.  
  
 El mapa de bits anterior se destruye automáticamente. Si la barra de título muestra un icono, porque se llama el [CMFCCaptionBar::SetIcon](#seticon) método, el mapa de bits no se mostrarán a menos que quite el icono mediante una llamada a [CMFCCaptionBar::RemoveIcon](#removeicon).  
  
 El mapa de bits se alinea según lo especificado por el *bmpAlignment* parámetro.  Este parámetro puede ser uno de los siguientes valores `BarElementAlignment`:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize  
 Establece el tamaño del borde de la barra de título.  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>Parámetros  
*nSize*<br/>
[in] El nuevo tamaño, en píxeles, del borde de barra de título.  
  
##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton  
 Establece el botón de la barra de título.  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszLabel*  
 La etiqueta del botón comando.  
  
 *uiCmdUI*  
 Identificador de comando. del botón  
  
 *btnAlignmnet*  
 Alineación del botón.  
  
 *bHasDropDownArrow*  
 TRUE si el botón muestra una flecha de lista desplegable.  
  
##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed  
 Especifica si se mantiene presionado el botón.  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPresed*  
 TRUE si el botón mantiene su estado presionado, FALSE en caso contrario.  
  
##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip  
 Establece la información sobre herramientas para el botón.  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszToolTip*<br/>
[in] El título de la información sobre herramientas.  
  
*lpszDescripción*<br/>
[in] La descripción de la información sobre herramientas.  
  
##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder  
 Establece el estilo de borde de la barra de título.  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
*bFlat*<br/>
[in] TRUE si el borde de una barra de título no tiene formato. FALSE si el borde 3D.  
  
##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon  
 Establece el icono para una barra de título.  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parámetros  
*hIcon*<br/>
[in] El identificador del icono para establecer.  
  
*iconAlignment*<br/>
[in] La alineación del icono.  
  
### <a name="remarks"></a>Comentarios  
 Barras de título pueden mostrar iconos o mapas de bits. Consulte [CMFCCaptionBar::SetBitmap](#setbitmap) para averiguar cómo mostrar un mapa de bits. Si establece un icono y un mapa de bits, siempre se muestra el icono. Llame a [CMFCCaptionBar::RemoveIcon](#removeicon) para quitar un icono de la barra de título.  
  
 El icono se alinea según el *iconAlignment* parámetro. Puede ser uno de los siguientes `BarElementAlignment` valores:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip  
 Establece la información sobre herramientas para la imagen en la barra de título.  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
*lpszToolTip*<br/>
[in] El texto de la información sobre herramientas.  
  
*lpszDescripción*<br/>
[in] La descripción de la información sobre herramientas.  
  
##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin  
 Establece la distancia entre el borde del elemento de barra de título y el borde del control de barra de título.  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>Parámetros  
*nMargin*<br/>
[in] La distancia, en píxeles, entre el borde de los elementos de la barra de título y el borde del control de barra de título.  
  
##  <a name="settext"></a>  CMFCCaptionBar::SetText  
 Establece la etiqueta de texto de la barra de título.  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Parámetros  
*strText*<br/>
[in] Para establecer la cadena de texto.  
  
*textAlignment*<br/>
[in] La alineación del texto.  
  
### <a name="remarks"></a>Comentarios  
 La etiqueta de texto se alinea según lo especificado por el *textAlignment* parámetro. Puede ser uno de los siguientes `BarElementAlignment` valores:  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
