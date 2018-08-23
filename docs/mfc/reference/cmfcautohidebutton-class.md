---
title: Clase CMFCAutoHideButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4cfc3e0d129fdb10ee10275000df6d8c51604be
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540707"
---
# <a name="cmfcautohidebutton-class"></a>Clase CMFCAutoHideButton
Botón que muestra u oculta una [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) configurada para ocultar.  

 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.    
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](#bringtotop)||  
|[CMFCAutoHideButton::Create](#create)|Crea e inicializa el botón de ocultación automática.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Recupera la alineación del botón de ocultación automática.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Devuelve el [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto asociado con el botón de ocultación automática.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Determina el tamaño del botón de ocultación automática.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Devuelve el tamaño de la etiqueta de texto para el botón de ocultación automática.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Resalta el botón de ocultación automática.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Indica si el botón de ocultación automática está activo.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Devuelve el estado de resaltado del botón de ocultación automática.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Determina si el botón de ocultación automática es horizontal o vertical.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Indica si el botón está visible.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|El marco de trabajo llama a este método cuando dibuja el botón de ocultación automática.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Muestra u oculta el asociado [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Muestra u oculta el botón de ocultación automática.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Comentarios  
 En la creación, la `CMFCAutoHideButton` objeto se asocia a un [CDockablePane Class](../../mfc/reference/cdockablepane-class.md). El objeto `CDockablePane` se oculta o se muestra cuando el usuario interactúa con el objeto `CMFCAutoHideButton`.  
  
 De forma predeterminada, el marco de trabajo crea automáticamente un `CMFCAutoHideButton` cuando el usuario activa la ocultación automática. El marco de trabajo puede crear un elemento de una clase de interfaz de usuario personalizada en lugar de la clase `CMFCAutoHideButton`. Para especificar qué clase de interfaz de usuario personalizada debería utilizar, establezca la variable de miembro estático `CMFCAutoHideBar::m_pAutoHideButtonRTS` igual que la clase de interfaz de usuario personalizada. De forma predeterminada, esta variable se establece en `CMFCAutoHideButton`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo construir un objeto `CMFCAutoHideButton` y usar varios métodos en la clase `CMFCAutoHideButton`. En el ejemplo se muestra cómo inicializar un objeto `CMFCAutoHideButton` mediante su método `Create`, mostrar la clase asociada `CDockablePane` y mostrar el botón de ocultación automática.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAutoHideButton`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxautohidebutton.h  
  
##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop  

  
```  
void BringToTop();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="create"></a>  CMFCAutoHideButton::Create  
 Crea e inicializa un botón de ocultación automática.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParentBar*  
 Un puntero a la barra de herramientas primario.  
  
 [in] *pAutoHideWnd*  
 Un puntero a un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto. Este botón de ocultación automática oculta y se muestra que `CDockablePane`.  
  
 [in] *dwAlignment*  
 Un valor que especifica la alineación del botón con la ventana de marco principal.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando creas un `CMFCAutoHideButton` objeto, debe asociar el botón de ocultación automática con un valor concreto `CDockablePane`. El usuario puede usar el botón de ocultación automática para ocultar y mostrar asociado `CDockablePane`.  
  
 El *dwAlignment* parámetro indica dónde reside el botón de ocultación automática en la aplicación. El parámetro puede establecerse en uno de los valores siguientes:  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CBRS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment  
 Recupera la alineación del botón de ocultación automática.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor DWORD que contiene la alineación actual del botón de ocultación automática.  
  
### <a name="remarks"></a>Comentarios  
 La alineación del botón de ocultación automática indica que el botón reside en la aplicación. Puede ser cualquiera de los siguientes valores:  
  
- CBRS_ALIGN_LEFT  
  
- CBRS_ALIGN_RIGHT  
  
- CRBS_ALIGN_TOP  
  
- CBRS_ALIGN_BOTTOM  
  
##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow  
 Devuelve el [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto asociado con el botón de ocultación automática.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la categoría asociada `CDockablePane` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para asociar un botón de ocultación automática con un `CDockablePane`, pase el `CDockablePane` como un parámetro a la [CMFCAutoHideButton::Create](#create) método.  
  
##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar  

  
```  
CMFCAutoHideBar* GetParentToolBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect  

  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize  
 Determina el tamaño del botón de ocultación automática.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene el tamaño del botón.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño calculado incluye el tamaño del borde del botón de ocultación automática.  
  
##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize  
 Devuelve el tamaño de la etiqueta de texto para el botón de ocultación automática.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el tamaño del texto del botón de ocultación automática.  
  
##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive  
 Indica si el botón de ocultación automática está activo.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón de ocultación automática está activo; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Un botón de ocultación automática está activo cuando asociado [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) se muestra la ventana.  
  
##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal  
 Determina si el botón de ocultación automática es horizontal o vertical.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el botón es horizontal; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo establece la orientación de un [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objeto al crearlo.  Puede controlar la orientación mediante la *dwAlignment* parámetro en el [CMFCAutoHideButton::Create](#create) método.  
  
##  <a name="istop"></a>  CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible  
 Indica si el botón de ocultación automática está visible.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón está visible; FALSE en caso contrario.  
  
##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw  
 El marco de trabajo llama a este método cuando dibuja el botón de ocultación automática.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Si desea personalizar la apariencia de los botones de ocultación automática en la aplicación, cree una clase nueva derivada de `CMFCAutoHideButton`. En la clase derivada, invalide este método.  
  
##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rectBounds*  
 El rectángulo delimitador del botón de ocultación automática.  
  
 [in] *rectBorderSize*  
 El grosor del borde de cada lado del botón de ocultación automática.  
  
### <a name="remarks"></a>Comentarios  
 Si desea personalizar el borde de cada botón de ocultación automática en la aplicación, cree una nueva clase que deriva el `CMFCAutoHideButton`. En la clase derivada, invalide este método.  
  
##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground  
 El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 El rectángulo delimitador del botón de ocultación automática.  
  
### <a name="remarks"></a>Comentarios  
 Si desea personalizar el fondo de los botones de ocultación automática en la aplicación, cree una nueva clase que deriva el `CMFCAutoHideButton`. En la clase derivada, invalide este método.  
  
##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow  
 Muestra u oculta el asociado [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bMostrar*  
 Un valor booleano que especifica si este método muestra el archivo adjunto `CDockablePane`.  
  
##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton  
 Muestra u oculta el botón de ocultación automática.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bMostrar*  
 Valor booleano que especifica si se debe mostrar el botón de ocultación automática.  
  
##  <a name="move"></a>  CMFCAutoHideButton::Move  

  
```  
void Move(int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nOffset*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane  

  
```  
void ReplacePane(CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pNewBar*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode  
 Permite deshabilitar el modo de ocultación automática.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pFirstBarInGroup*  
 Puntero a la primera barra del grupo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton  
 Resalta el botón Ocultar automáticamente.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parámetros  
 *bHighlight*  
 Especifica el auto nuevo ocultar el estado de botón. TRUE indica que el botón está resaltado, FALSE indica que no se resalta el botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted  
 Devuelve el estado de resaltado del botón Ocultar automáticamente.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el auto oculta botón está resaltado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCAutoHideBar (clase)](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite (clase)](../../mfc/reference/cautohidedocksite-class.md)
