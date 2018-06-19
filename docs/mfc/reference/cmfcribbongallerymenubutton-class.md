---
title: Clase CMFCRibbonGalleryMenuButton | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27d2d4e95bffa3bd074ca1c6d4bf6d9c7e095a56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370912"
---
# <a name="cmfcribbongallerymenubutton-class"></a>Clase CMFCRibbonGalleryMenuButton
Implementa un botón de menú de la cinta que contiene galerías de la cinta.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|Construye e inicializa un objeto `CMFCRibbonGalleryMenuButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(Invalida [cmfctoolbarmenubutton:: CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom).)|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(Invalida [cmfctoolbarmenubutton:: CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu).)|  
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||  
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|(Invalida `CMFCToolBarMenuButton::HasButton`).|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(Invalida [cmfctoolbarmenubutton:: Isemptymenuallowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed).)|  
  
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
  
##  <a name="copyfrom"></a>  CMFCRibbonGalleryMenuButton::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cmfcribbongallerymenubutton"></a>  CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton  
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
 El identificador de comando del botón. Este es el valor enviado la **WM_COMMAND** mensaje cuando el usuario hace clic en este botón.  
  
 `iImage`  
 El índice de la imagen para mostrar con el botón de menú de la galería. Las imágenes se almacenan en la `imagesPalette` parámetro.  
  
 `lpszText`  
 El texto para mostrar en el botón de menú.  
  
 `imagesPalette`  
 Contiene la lista de imágenes que se muestran en la galería.  
  
 `uiImagesPaletteResID`  
 El identificador de recurso de la lista de imágenes para las imágenes para mostrar en la galería.  
  
 `cxPaletteImage`  
 Especifica el ancho en píxeles de la imagen que se muestra en la galería.  
  
### <a name="remarks"></a>Comentarios  
 El botón de menú de la galería se muestra como un menú emergente con una flecha. Cuando el usuario hace clic en este botón, se abre una galería de imágenes.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el constructor de la `CMFCRibbonGalleryMenuButton` clase. Este fragmento de código forma parte de la [ejemplo de demostración de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]  
  
##  <a name="createpopupmenu"></a>  CMFCRibbonGalleryMenuButton::CreatePopupMenu  

  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpalette"></a>  CMFCRibbonGalleryMenuButton::GetPalette  

  
```  
CMFCRibbonGallery& GetPalette();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasbutton"></a>  CMFCRibbonGalleryMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isemptymenuallowed"></a>  CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed  

  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery (clase)](../../mfc/reference/cmfcribbongallery-class.md)
