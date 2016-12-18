---
title: "CMFCRibbonUndoButton Class | Microsoft Docs"
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
  - "CMFCRibbonUndoButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonUndoButton class"
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonUndoButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonUndoButton` implementa un botón de lista desplegable que contiene los comandos más recientes del usuario.  Los usuarios pueden seleccionar uno o más de los comandos más recientes de la lista desplegable para deshacer o rehacer para deshacer ellas.  
  
## Sintaxis  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](../Topic/CMFCRibbonUndoButton::CMFCRibbonUndoButton.md)|Construye un nuevo objeto de `CMFCRibbonUndoButton` utilizando el identificador de comando especificado, la etiqueta de texto e imágenes de la lista del objeto primario.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](../Topic/CMFCRibbonUndoButton::AddUndoAction.md)|Agrega una nueva acción a la lista de acciones.|  
|[CMFCRibbonUndoButton::CleanUpUndoList](../Topic/CMFCRibbonUndoButton::CleanUpUndoList.md)|Borra la lista de acciones, que es la lista desplegable.|  
|[CMFCRibbonUndoButton::GetActionNumber](../Topic/CMFCRibbonUndoButton::GetActionNumber.md)|determina el número de elementos que un usuario seleccionado de la lista desplegable.|  
|[CMFCRibbonUndoButton::HasMenu](../Topic/CMFCRibbonUndoButton::HasMenu.md)|indica si el objeto contiene un menú.|  
  
## Comentarios  
 La clase de `CMFCRibbonUndoButton` utiliza una pila para representar la lista desplegable.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCRibbonUndoButton` , y agrega una nueva acción a la lista de acciones.  Este fragmento de código es parte de [ejemplo de Gadgets de la cinta de opciones](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/CPP/cmfcribbonundobutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## Requisitos  
 **encabezado:** afxribbonundobutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)