---
title: "CMFCRibbonApplicationButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonApplicationButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonApplicationButton class"
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCRibbonApplicationButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

implementa un botón especial situado en la esquina superior izquierda de la ventana de la aplicación.  Cuando se hace clic en, el botón abre un menú que contiene normalmente los comandos comunes de **Archivo** como **Abrir**, **Guardar**, y **Salir**.  
  
## Sintaxis  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](../Topic/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton.md)|Las construcciones e inicializan un objeto de `CMFCRibbonApplicationButton` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCRibbonApplicationButton::SetImage](../Topic/CMFCRibbonApplicationButton::SetImage.md)|Asigna una imagen al botón de la aplicación de la cinta de opciones.|  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonApplicationButton` .  El ejemplo muestra cómo asignar una imagen al botón de la aplicación, y cómo establecer su información sobre herramientas.  Este fragmento de código es parte de [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonBar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)