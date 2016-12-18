---
title: "CMFCRibbonGalleryMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonGalleryMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGalleryMenuButton class"
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonGalleryMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un botón de menú de la cinta que contiene galerías de la cinta.  
  
## Sintaxis  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](../Topic/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton.md)|Construye e inicializa un objeto `CMFCRibbonGalleryMenuButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](../Topic/CMFCRibbonGalleryMenuButton::CopyFrom.md)|\(Invalida [CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)\).|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](../Topic/CMFCRibbonGalleryMenuButton::CreatePopupMenu.md)|\(Invalida [CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)\).|  
|[CMFCRibbonGalleryMenuButton::GetPalette](../Topic/CMFCRibbonGalleryMenuButton::GetPalette.md)||  
|[CMFCRibbonGalleryMenuButton::HasButton](../Topic/CMFCRibbonGalleryMenuButton::HasButton.md)|\(Invalida `CMFCToolBarMenuButton::HasButton`\).|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](../Topic/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed.md)|\(Invalida [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)\).|  
  
### Comentarios  
 El botón de menú de la galería se muestra como un menú emergente con una flecha.  Cuando el usuario hace clic en este botón, se abre una galería de imágenes.  Cuando se crea un botón de menú de la galería, hay que especificar una lista de imágenes que contenga esas imágenes.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo mostrar una galería de viñetas en un botón de menú:  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);  
    if (nBulletIndex >= 0)  
    {  
        CMFCToolBarButton* pExButton =  
            pMenuBar->GetButton(nBulletIndex);  
        ASSERT_VALID (pExButton);  
        CMFCRibbonGalleryMenuButton paletteBullet (  
            pExButton->m_nID,  
            pExButton->GetImage (),  
            pExButton->m_strText);  
        InitBulletPalette (&paletteBullet.GetPalette ());  
        pMenuBar->ReplaceButton (ID_PARA_BULLETS, paletteBullet);  
    }  
}  
```  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxRibbonPaletteGallery.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)