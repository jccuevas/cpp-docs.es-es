---
title: "CMFCToolBarFontSizeComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarFontSizeComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontSizeComboBox class"
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCToolBarFontSizeComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón de la barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar un tamaño de fuente.  
  
## Sintaxis  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](../Topic/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox.md)|Crea un objeto `CMFCToolBarFontSizeComboBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::GetTwipSize.md)|devuelve el tamaño de fuente seleccionado en twips.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md)|Rellena la lista del cuadro combinado con todos los tamaños de fuente compatibles para una fuente especificada.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::SetTwipSize.md)|establece el tamaño de fuente en twips.|  
  
## Comentarios  
 Puede utilizar un objeto de `CMFCToolBarFontSizeComboBox` junto con un objeto de [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) para permitir a un usuario seleccionar una fuente y un tamaño de fuente.  
  
 Puede agregar un botón del cuadro combinado del tamaño de fuente a una barra de herramientas igual que agrega un botón del cuadro combinado de la fuente.  Para obtener más información, vea [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Cuando el usuario selecciona una nueva fuente en un objeto de `CMFCToolBarFontComboBox` , puede rellenar el cuadro combinado del tamaño de fuente con tamaños admitidos para esa fuente utilizando el método de [CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md) .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCToolBarFontSizeComboBox` para configurar un objeto de `CMFCToolBarFontSizeComboBox` .  El ejemplo muestra cómo recuperar el tamaño de fuente, en twips, textbox, rellena el cuadro combinado del tamaño de fuente con todos los tamaños válidos de fuente especificado, y especifica el tamaño de fuente en twips.  Este fragmento de código es parte de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/CPP/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarfontcombobox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)