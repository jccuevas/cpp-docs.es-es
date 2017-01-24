---
title: "CMFCRibbonFontComboBox Class | Microsoft Docs"
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
  - "CMFCRibbonFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonFontComboBox class"
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un cuadro combinado que contiene una lista de fuentes.  El cuadro combinado se coloca en un panel de la cinta.  
  
## Sintaxis  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructor.|  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](../Topic/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox.md)|Construye e inicializa un objeto `CMFCRibbonFontComboBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](../Topic/CMFCRibbonFontComboBox::BuildFonts.md)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia especificados.|  
|`CMFCRibbonFontComboBox::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonFontComboBox::GetCharSet](../Topic/CMFCRibbonFontComboBox::GetCharSet.md)|Devuelve el juego de caracteres especificado.|  
|[CMFCRibbonFontComboBox::GetFontDesc](../Topic/CMFCRibbonFontComboBox::GetFontDesc.md)||  
|[CMFCRibbonFontComboBox::GetFontType](../Topic/CMFCRibbonFontComboBox::GetFontType.md)|Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado.  Las opciones válidas son DEVICE\_FONTTYPE, RASTER\_FONTTYPE y TRUETYPE\_FONTTYPE o cualquier combinación bit a bit de estas.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](../Topic/CMFCRibbonFontComboBox::GetPitchAndFamily.md)|Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Usado por el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|[CMFCRibbonFontComboBox::RebuildFonts](../Topic/CMFCRibbonFontComboBox::RebuildFonts.md)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|  
|[CMFCRibbonFontComboBox::SetFont](../Topic/CMFCRibbonFontComboBox::SetFont.md)|Selecciona la fuente especificada en el cuadro combinado.|  
  
## Comentarios  
 Después de crear un objeto `CMFCRibbonFontComboBox`, agréguelo a un panel de la cinta llamando a [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## Requisitos  
 **Encabezado:** afxRibbonComboBox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox Class](../../mfc/reference/cmfcribboncombobox-class.md)