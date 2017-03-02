---
title: Clase CMFCRibbonGalleryMenuButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGalleryMenuButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton class
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dce01ac22db0ff28e8f07b6d30f6418a61ad68d5
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbongallerymenubutton-class"></a>Clase CMFCRibbonGalleryMenuButton
Implementa un botón de menú de la cinta que contiene galerías de la cinta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Construye e inicializa un objeto `CMFCRibbonGalleryMenuButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Invalida [CMFCToolBarMenuButton::CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom).)|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Invalida [CMFCToolBarMenuButton::CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|  
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||  
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Invalida `CMFCToolBarMenuButton::HasButton`).|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Invalida [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|  
  
### <a name="remarks"></a>Comentarios  
 El botón de menú de la galería se muestra como un menú emergente con una flecha. Cuando el usuario hace clic en este botón, se abre una galería de imágenes. Cuando se crea un botón de menú de la galería, hay que especificar una lista de imágenes que contenga esas imágenes.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo mostrar una galería de viñetas en un botón de menú:  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)  
 {  
    CMFCToolBarButton* pExButton = 
    pMenuBar->GetButton(nBulletIndex);
ASSERT_VALID (pExButton);

    CMFCRibbonGalleryMenuButton paletteBullet (
    pExButton->m_nID, 
    pExButton->GetImage (),  
    pExButton->m_strText);

 InitBulletPalette (&paletteBullet.GetPalette ());

    pMenuBar->ReplaceButton (ID_PARA_BULLETS,
    paletteBullet);

 }  
}  
```  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonPaletteGallery.h  
  
##  <a name="a-namecopyfroma--cmfcribbongallerymenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCRibbonGalleryMenuButton::CopyFrom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecmfcribbongallerymenubuttona--cmfcribbongallerymenubuttoncmfcribbongallerymenubutton"></a><a name="cmfcribbongallerymenubutton"></a>CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton  
 Construye e inicializa un [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md) objeto.  
  
```  
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    UINT uiImagesPaletteResID = 0,  
    int cxPaletteImage = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `uiID`  
 El identificador de comando del botón. Este es el valor que se envía en el **WM_COMMAND** mensaje cuando el usuario hace clic en este botón.  
  
 `iImage`  
 El índice de la imagen para mostrar con el botón de menú de la galería. Las imágenes se almacenan en la `imagesPalette` parámetro.  
  
 `lpszText`  
 Texto que se va a mostrar en el botón de menú.  
  
 `imagesPalette`  
 Contiene la lista de imágenes que se muestran en la galería.  
  
 `uiImagesPaletteResID`  
 El identificador de recurso de la lista de imágenes para las imágenes para mostrar en la galería.  
  
 `cxPaletteImage`  
 Especifica el ancho en píxeles de la imagen para mostrar en la galería.  
  
### <a name="remarks"></a>Comentarios  
 El botón de menú de la galería se muestra como un menú emergente que tiene una flecha. Cuando el usuario hace clic en este botón, se abre una galería de imágenes.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el constructor de la `CMFCRibbonGalleryMenuButton` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Microsoft Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo Nº&8;](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]  
  
##  <a name="a-namecreatepopupmenua--cmfcribbongallerymenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCRibbonGalleryMenuButton::CreatePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpalettea--cmfcribbongallerymenubuttongetpalette"></a><a name="getpalette"></a>CMFCRibbonGalleryMenuButton::GetPalette  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonGallery& GetPalette();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehasbuttona--cmfcribbongallerymenubuttonhasbutton"></a><a name="hasbutton"></a>CMFCRibbonGalleryMenuButton::HasButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisemptymenualloweda--cmfcribbongallerymenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Clase CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

