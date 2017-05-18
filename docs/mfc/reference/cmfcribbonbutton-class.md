---
title: Clase CMFCRibbonButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton::CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton::AddSubItem
- AFXRIBBONBUTTON/CMFCRibbonButton::CanBeStretched
- AFXRIBBONBUTTON/CMFCRibbonButton::CleanUpSizes
- AFXRIBBONBUTTON/CMFCRibbonButton::ClosePopupMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawBottomText
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawImage
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawRibbonText
- AFXRIBBONBUTTON/CMFCRibbonButton::FindSubItemIndexByID
- AFXRIBBONBUTTON/CMFCRibbonButton::GetCommandRect
- AFXRIBBONBUTTON/CMFCRibbonButton::GetCompactSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetIcon
- AFXRIBBONBUTTON/CMFCRibbonButton::GetImageIndex
- AFXRIBBONBUTTON/CMFCRibbonButton::GetImageSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetIntermediateSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::GetMenuRect
- AFXRIBBONBUTTON/CMFCRibbonButton::GetRegularSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetSubItems
- AFXRIBBONBUTTON/CMFCRibbonButton::GetTextRowHeight
- AFXRIBBONBUTTON/CMFCRibbonButton::GetToolTipText
- AFXRIBBONBUTTON/CMFCRibbonButton::HasCompactMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasIntermediateMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasLargeMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::IsAlwaysDrawBorder
- AFXRIBBONBUTTON/CMFCRibbonButton::IsAlwaysLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsApplicationButton
- AFXRIBBONBUTTON/CMFCRibbonButton::IsCommandAreaHighlighted
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDefaultCommand
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDefaultPanelButton
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDrawTooltipImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsMenuAreaHighlighted
- AFXRIBBONBUTTON/CMFCRibbonButton::IsMenuOnBottom
- AFXRIBBONBUTTON/CMFCRibbonButton::IsPopupDefaultMenuLook
- AFXRIBBONBUTTON/CMFCRibbonButton::IsRightAlignMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::IsSingleLineText
- AFXRIBBONBUTTON/CMFCRibbonButton::OnCalcTextSize
- AFXRIBBONBUTTON/CMFCRibbonButton::OnDrawBorder
- AFXRIBBONBUTTON/CMFCRibbonButton::OnDraw
- AFXRIBBONBUTTON/CMFCRibbonButton::OnFillBackground
- AFXRIBBONBUTTON/CMFCRibbonButton::RemoveAllSubItems
- AFXRIBBONBUTTON/CMFCRibbonButton::RemoveSubItem
- AFXRIBBONBUTTON/CMFCRibbonButton::SetACCData
- AFXRIBBONBUTTON/CMFCRibbonButton::SetAlwaysLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::SetDefaultCommand
- AFXRIBBONBUTTON/CMFCRibbonButton::SetDescription
- AFXRIBBONBUTTON/CMFCRibbonButton::SetImageIndex
- AFXRIBBONBUTTON/CMFCRibbonButton::SetMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::SetParentCategory
- AFXRIBBONBUTTON/CMFCRibbonButton::SetRightAlignMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::SetText
- AFXRIBBONBUTTON/CMFCRibbonButton::OnClick
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButton class
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
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
ms.openlocfilehash: 08672f10cf67a773f2af8d12130c4e3f5b497e11
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbutton-class"></a>Clase CMFCRibbonButton
La clase `CMFCRibbonButton` implementa botones que puede colocar en elementos de barra de cinta como paneles, barras de herramientas de acceso rápido y menús emergentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::CMFCRibbonButton](#cmfcribbonbutton)|Construye un objeto de botón de la cinta.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::AddSubItem](#addsubitem)|Agrega un elemento de menú al menú emergente asociado al botón.|  
|[CMFCRibbonButton::CanBeStretched](#canbestretched)|(Invalida [CMFCRibbonBaseElement::CanBeStretched](../../mfc/reference/cmfcribbonbaseelement-class.md#canbestretched).)|  
|[CMFCRibbonButton::CleanUpSizes](#cleanupsizes)|(Invalida [CMFCRibbonBaseElement::CleanUpSizes](../../mfc/reference/cmfcribbonbaseelement-class.md#cleanupsizes).)|  
|[CMFCRibbonButton::ClosePopupMenu](#closepopupmenu)|(Invalida [CMFCRibbonBaseElement::ClosePopupMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#closepopupmenu).)|  
|[CMFCRibbonButton::DrawBottomText](#drawbottomtext)||  
|[CMFCRibbonButton::DrawImage](#drawimage)|(Invalida [CMFCRibbonBaseElement::DrawImage](../../mfc/reference/cmfcribbonbaseelement-class.md#drawimage).)|  
|[CMFCRibbonButton::DrawRibbonText](#drawribbontext)||  
|[CMFCRibbonButton::FindSubItemIndexByID](#findsubitemindexbyid)|Devuelve el índice de un elemento de menú emergente asociado al id. de comando especificado.|  
|[CMFCRibbonButton::GetCommandRect](#getcommandrect)||  
|[CMFCRibbonButton::GetCompactSize](#getcompactsize)|Devuelve el tamaño compacto del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetCompactSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getcompactsize).)|  
|[CMFCRibbonButton::GetIcon](#geticon)||  
|[CMFCRibbonButton::GetImageIndex](#getimageindex)|Devuelve el índice de la imagen asociada al botón.|  
|[CMFCRibbonButton::GetImageSize](#getimagesize)|Devuelve el tamaño de la imagen del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|  
|[CMFCRibbonButton::GetIntermediateSize](#getintermediatesize)|Devuelve el tamaño del elemento de la cinta en su estado intermedio. (Invalida [CMFCRibbonBaseElement::GetIntermediateSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getintermediatesize).)|  
|[CMFCRibbonButton::GetMenu](#getmenu)|Devuelve un controlador a un menú de Windows que se asigna al botón de la cinta.|  
|[CMFCRibbonButton::GetMenuRect](#getmenurect)||  
|[CMFCRibbonButton::GetRegularSize](#getregularsize)|Devuelve el tamaño normal del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonButton::GetSubItems](#getsubitems)||  
|[CMFCRibbonButton::GetTextRowHeight](#gettextrowheight)||  
|[CMFCRibbonButton::GetToolTipText](#gettooltiptext)|Devuelve el texto de información sobre herramientas del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::GetToolTipText](../../mfc/reference/cmfcribbonbaseelement-class.md#gettooltiptext).)|  
|[CMFCRibbonButton::HasCompactMode](#hascompactmode)|Especifica si el elemento de la cinta tiene un modo compacto. (Invalida [CMFCRibbonBaseElement::HasCompactMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hascompactmode).)|  
|[CMFCRibbonButton::HasIntermediateMode](#hasintermediatemode)|Especifica si el elemento de la cinta tiene un modo intermedio. (Invalida [CMFCRibbonBaseElement::HasIntermediateMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hasintermediatemode).)|  
|[CMFCRibbonButton::HasLargeMode](#haslargemode)|Determina si el elemento de la cinta tiene un modo grande. (Invalida [CMFCRibbonBaseElement::HasLargeMode](../../mfc/reference/cmfcribbonbaseelement-class.md#haslargemode).)|  
|[CMFCRibbonButton::HasMenu](#hasmenu)|(Invalida [CMFCRibbonBaseElement::HasMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#hasmenu).)|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](#isalwaysdrawborder)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](#isalwayslargeimage)|(Invalida [CMFCRibbonBaseElement::IsAlwaysLargeImage](../../mfc/reference/cmfcribbonbaseelement-class.md#isalwayslargeimage).)|  
|[CMFCRibbonButton::IsApplicationButton](#isapplicationbutton)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](#iscommandareahighlighted)||  
|[CMFCRibbonButton::IsDefaultCommand](#isdefaultcommand)|Determina si se ha habilitado el comando predeterminado de un botón de la cinta.|  
|[CMFCRibbonButton::IsDefaultPanelButton](#isdefaultpanelbutton)||  
|[CMFCRibbonButton::IsDrawTooltipImage](#isdrawtooltipimage)||  
|[CMFCRibbonButton::IsLargeImage](#islargeimage)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](#ismenuareahighlighted)||  
|[CMFCRibbonButton::IsMenuOnBottom](#ismenuonbottom)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](#ispopupdefaultmenulook)||  
|[CMFCRibbonButton::IsRightAlignMenu](#isrightalignmenu)|Determina si el menú está alineado a la derecha.|  
|[CMFCRibbonButton::IsSingleLineText](#issinglelinetext)||  
|[CMFCRibbonButton::OnCalcTextSize](#oncalctextsize)|(Invalida [CMFCRibbonBaseElement::OnCalcTextSize](../../mfc/reference/cmfcribbonbaseelement-class.md#oncalctextsize).)|  
|[CMFCRibbonButton::OnDrawBorder](#ondrawborder)||  
|[CMFCRibbonButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el elemento de la cinta. (Invalida [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonButton::OnFillBackground](#onfillbackground)||  
|[CMFCRibbonButton::RemoveAllSubItems](#removeallsubitems)|Quita todos los elementos del menú emergente.|  
|[CMFCRibbonButton::RemoveSubItem](#removesubitem)|Quita un elemento del menú emergente.|  
|[CMFCRibbonButton::SetACCData](#setaccdata)|(Invalida [CMFCRibbonBaseElement::SetACCData](../../mfc/reference/cmfcribbonbaseelement-class.md#setaccdata).)|  
|[CMFCRibbonButton::SetAlwaysLargeImage](#setalwayslargeimage)|Especifica si el botón muestra una imagen grande o pequeña cuando el usuario lo contrae.|  
|[CMFCRibbonButton::SetDefaultCommand](#setdefaultcommand)|Habilita el comando predeterminado del botón de la cinta.|  
|[CMFCRibbonButton::SetDescription](#setdescription)|Establece la descripción del elemento de la cinta. (Invalida [CMFCRibbonBaseElement::SetDescription](../../mfc/reference/cmfcribbonbaseelement-class.md#setdescription).)|  
|[CMFCRibbonButton::SetImageIndex](#setimageindex)|Asigna un índice a la imagen del botón.|  
|[CMFCRibbonButton::SetMenu](#setmenu)|Asigna un menú emergente al botón de la cinta.|  
|[CMFCRibbonButton::SetParentCategory](#setparentcategory)|(Invalida [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|  
|[CMFCRibbonButton::SetRightAlignMenu](#setrightalignmenu)|Alinea el menú emergente a la derecha del botón.|  
|[CMFCRibbonButton::SetText](#settext)|Establece el texto para el elemento de la cinta. (Invalida [CMFCRibbonBaseElement::SetText](../../mfc/reference/cmfcribbonbaseelement-class.md#settext).)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::OnClick](#onclick)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonButton`. En el ejemplo se muestra cómo construir un objeto de la clase `CMFCRibbonButton`, asignar un menú emergente al botón de la cinta, establecer la descripción del botón, quitar un elemento del menú emergente y alinear a la derecha el menú emergente hacia el borde del botón.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#7;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_1.cpp)]  
  
## <a name="remarks"></a>Comentarios  
 Para usar un botón de la cinta de opciones en una aplicación, construya el objeto de botón y agregarlo a la cinta de opciones adecuada [panel](../../mfc/reference/cmfcribbonpanel-class.md).  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"), // Panel name  
    m_PanelIcons.ExtractIcon (0)); // Panel icon  

// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton = 
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);

// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);

// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));
```  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribbonbutton.h  
  
##  <a name="addsubitem"></a>CMFCRibbonButton::AddSubItem  
 Agrega un elemento de menú al menú emergente asociado al botón.  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pSubItem`  
 Especifica un puntero para el nuevo elemento para agregar.  
  
 [in] `nIndex`  
 Especifica el índice en el que se va a agregar el elemento a la matriz de elementos de menú del botón; -1 para agregar el elemento al final de la matriz de elementos de menú.  
  
##  <a name="canbestretched"></a>CMFCRibbonButton::CanBeStretched  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cleanupsizes"></a>CMFCRibbonButton::CleanUpSizes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUpSizes();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="closepopupmenu"></a>CMFCRibbonButton::ClosePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClosePopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cmfcribbonbutton"></a>CMFCRibbonButton::CMFCRibbonButton  
 Construye un objeto de botón de la cinta.  
  
```  
CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1,  
    BOOL bAlwaysShowDescription=FALSE);

CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon,  
    BOOL bAlwaysShowDescription=FALSE,  
    HICON hIconSmall=NULL,  
    BOOL bAutoDestroyIcon=FALSE,  
    BOOL bAlphaBlendIcon=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador de comando del botón.  
  
 [in] `lpszText`  
 Especifica la etiqueta de texto del botón.  
  
 [in] `nSmallImageIndex`  
 Especifica un índice de base cero de la imagen del botón pequeño en la lista de imágenes de la categoría primaria.  
  
 [in] `nLargeImageIndex`  
 Especifica un índice de base cero de la imagen del botón grande en la lista de imágenes de la categoría primaria.  
  
 [in] `hIcon`  
 Especifica un identificador para el icono de la aplicación como la imagen del botón.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCRibbonButton` objeto.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&6;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_2.cpp)]  
  
##  <a name="drawbottomtext"></a>CMFCRibbonButton::DrawBottomText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CSize DrawBottomText(
    CDC* pDC,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `bCalcOnly`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="drawimage"></a>CMFCRibbonButton::DrawImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void DrawImage(
    CDC* pDC,  
    RibbonImageType type,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `type`  
 [in] `rectImage`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="drawribbontext"></a>CMFCRibbonButton::DrawRibbonText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int DrawRibbonText(
    CDC* pDC,  
    const CString& strText,  
    CRect rectText,  
    UINT uiDTFlags,  
    COLORREF clrText = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `strText`  
 [in] `rectText`  
 [in] `uiDTFlags`  
 [in] `clrText`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findsubitemindexbyid"></a>CMFCRibbonButton::FindSubItemIndexByID  
 Devuelve el índice de un elemento de menú emergente asociado al id. de comando especificado.  
  
```  
int FindSubItemIndexByID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 Especifica el identificador de comando del elemento de menú emergente.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento secundario que está asociado el `uiID`. -1 si no hay ningún elemento de subproceso.  
  
##  <a name="getcommandrect"></a>CMFCRibbonButton::GetCommandRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetCommandRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcompactsize"></a>CMFCRibbonButton::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="geticon"></a>CMFCRibbonButton::GetIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HICON GetIcon(BOOL bLargeIcon = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLargeIcon`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getimageindex"></a>CMFCRibbonButton::GetImageIndex  
 Devuelve el índice de la imagen asociada al botón.  
  
```  
int GetImageIndex(BOOL bLargeImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLargeImage`  
 Si `TRUE`, devuelve el índice de imagen en la lista de imágenes que contiene las imágenes grandes; en caso contrario devuelve el índice de imagen en la lista de imágenes que contiene las imágenes pequeñas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la imagen del botón en la lista de imágenes asociada.  
  
##  <a name="getimagesize"></a>CMFCRibbonButton::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize(RibbonImageType type) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `type`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getintermediatesize"></a>CMFCRibbonButton::GetIntermediateSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmenu"></a>CMFCRibbonButton::GetMenu  
 Devuelve un controlador a un menú de Windows que se asigna al botón de la cinta.  
  
```  
HMENU GetMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un menú de Windows asignado al botón; `NULL` si no hay ningún menú asignado.  
  
##  <a name="getmenurect"></a>CMFCRibbonButton::GetMenuRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetMenuRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getregularsize"></a>CMFCRibbonButton::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getsubitems"></a>CMFCRibbonButton::GetSubItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& GetSubItems() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettextrowheight"></a>CMFCRibbonButton::GetTextRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTextRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettooltiptext"></a>CMFCRibbonButton::GetToolTipText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hascompactmode"></a>CMFCRibbonButton::HasCompactMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasintermediatemode"></a>CMFCRibbonButton::HasIntermediateMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasIntermediateMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="haslargemode"></a>CMFCRibbonButton::HasLargeMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasmenu"></a>CMFCRibbonButton::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isalwaysdrawborder"></a>CMFCRibbonButton::IsAlwaysDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysDrawBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isalwayslargeimage"></a>CMFCRibbonButton::IsAlwaysLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysLargeImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isapplicationbutton"></a>CMFCRibbonButton::IsApplicationButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsApplicationButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="iscommandareahighlighted"></a>CMFCRibbonButton::IsCommandAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsCommandAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdefaultcommand"></a>CMFCRibbonButton::IsDefaultCommand  
 Especifica si está habilitado el comando predeterminado para un botón de la cinta de opciones.  
  
```  
BOOL IsDefaultCommand() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si ha habilitado el comando predeterminado para un botón de la cinta de opciones; `FALSE` en caso contrario.  
  
##  <a name="isdefaultpanelbutton"></a>CMFCRibbonButton::IsDefaultPanelButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDefaultPanelButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonButton::IsDrawTooltipImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="islargeimage"></a>CMFCRibbonButton::IsLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsLargeImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenuareahighlighted"></a>CMFCRibbonButton::IsMenuAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsMenuAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenuonbottom"></a>CMFCRibbonButton::IsMenuOnBottom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuOnBottom() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ispopupdefaultmenulook"></a>CMFCRibbonButton::IsPopupDefaultMenuLook  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsPopupDefaultMenuLook() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isrightalignmenu"></a>CMFCRibbonButton::IsRightAlignMenu  
 Especifica si el menú está alineado a la derecha.  
  
```  
BOOL IsRightAlignMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú está alineado a la derecha; de lo contrario, `FALSE`.  
  
##  <a name="issinglelinetext"></a>CMFCRibbonButton::IsSingleLineText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsSingleLineText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncalctextsize"></a>CMFCRibbonButton::OnCalcTextSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnCalcTextSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclick"></a>CMFCRibbonButton::OnClick  
 Llamado por el marco de trabajo cuando el usuario hace clic en el botón.  
  
```  
virtual void OnClick(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica la posición del clic del mouse.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea controlar el evento.  
  
##  <a name="ondraw"></a>CMFCRibbonButton::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawborder"></a>CMFCRibbonButton::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onfillbackground"></a>CMFCRibbonButton::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removeallsubitems"></a>CMFCRibbonButton::RemoveAllSubItems  
 Quita todos los elementos del menú emergente.  
  
```  
void RemoveAllSubItems();
```  
  
##  <a name="removesubitem"></a>CMFCRibbonButton::RemoveSubItem  
 Quita un elemento del menú emergente.  
  
```  
BOOL RemoveSubItem(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de base cero del elemento de menú que desea quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento especificado se ha quitado correctamente; de lo contrario, `FALSE` si `nIndex` es negativo o supera el número de elementos de menú en el menú emergente.  
  
##  <a name="setaccdata"></a>CMFCRibbonButton::SetACCData  
 Establece los datos de accesibilidad para el botón de la cinta de opciones.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);  
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 La ventana principal para el elemento de la cinta de opciones.  
  
 `data`  
 Los datos de accesibilidad para el elemento de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setalwayslargeimage"></a>CMFCRibbonButton::SetAlwaysLargeImage  
 Especifica si el botón muestra una imagen grande o pequeña cuando el usuario lo contrae.  
  
```  
void SetAlwaysLargeImage(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 Si `TRUE`, el botón muestra una imagen grande. De lo contrario, el botón muestra una imagen pequeña.  
  
##  <a name="setdefaultcommand"></a>CMFCRibbonButton::SetDefaultCommand  
 Habilita el comando predeterminado del botón de la cinta.  
  
```  
void SetDefaultCommand(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 Si `TRUE`, el botón puede ejecutar el comando predeterminado. Si `FALSE`, el botón no puede ejecutar el comando predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 `bSet`es relevante sólo cuando el botón tiene un menú. Si `bSet` es `TRUE`, el botón puede ejecutar su comando de forma predeterminada y el menú emergente asignado aparece sólo cuando un usuario hace clic en la flecha situada en el borde derecho del botón. De lo contrario, el botón no puede ejecutar el comando predeterminado, y aparece el menú emergente, independientemente de qué área del botón hace clic el usuario.  
  
##  <a name="setdescription"></a>CMFCRibbonButton::SetDescription  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetDescription(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setimageindex"></a>CMFCRibbonButton::SetImageIndex  
 Asigna un índice a la imagen del botón.  
  
```  
void SetImageIndex(
    int nIndex,  
    BOOL bLargeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice de la imagen.  
  
 [in] `bLargeImage`  
 Si `TRUE`, el índice especificado hace referencia a la lista de imágenes de gran tamaño. De lo contrario, el índice hace referencia a la lista de las imágenes pequeñas.  
  
##  <a name="setmenu"></a>CMFCRibbonButton::SetMenu  
 Asigna un menú emergente al botón de la cinta.  
  
```  
void SetMenu(
    HMENU hMenu,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);

void SetMenu(
    UINT uiMenuResID,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMenu`  
 Identificador de un menú de Windows.  
  
 `bIsDefaultCommand`  
 Si `TRUE`, el botón puede ejecutar el comando predeterminado; en caso contrario, el botón muestra un menú emergente.  
  
 `bRightAlign`  
 Si `TRUE`, el menú está alineado a la derecha. De lo contrario, el menú está alineado a la izquierda.  
  
 `uiMenuResID`  
 Un identificador de recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 Cuando la aplicación asigna el menú al botón, el botón muestra una flecha en su lado derecho. Si `bIsDefaultCommand` es `TRUE`, el menú aparece sólo cuando el usuario hace clic en la flecha. Si el usuario hace clic en el botón, se ejecuta el comando predeterminado. Si `bIsDefaultCommand` es `FALSE`, aparece el menú, haga clic en cualquier lugar en el botón.  
  
##  <a name="setparentcategory"></a>CMFCRibbonButton::SetParentCategory  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setrightalignmenu"></a>CMFCRibbonButton::SetRightAlignMenu  
 Alinea el menú emergente para el borde del botón.  
  
```  
void SetRightAlignMenu(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 Si `TRUE`, el menú está alineado a la derecha. De lo contrario, el menú está alineado a la izquierda  
  
##  <a name="settext"></a>CMFCRibbonButton::SetText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

