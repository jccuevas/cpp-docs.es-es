---
title: "CMFCRibbonEdit Class | Microsoft Docs"
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
  - "CMFCRibbonEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonEdit class"
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un control de edición que se encuentra en una barra de la cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|Crea un objeto `CMFCRibbonEdit`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](../Topic/CMFCRibbonEdit::CanBeStretched.md)|Indica si el alto del control de `CMFCRibbonEdit` puede aumentar verticalmente el alto de una fila de la cinta de opciones.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|Crea un objeto `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::CopyFrom](../Topic/CMFCRibbonEdit::CopyFrom.md)|Copia el estado del objeto especificado de `CMFCRibbonEdit` al objeto actual de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::CreateEdit](../Topic/CMFCRibbonEdit::CreateEdit.md)|crea un nuevo cuadro de texto para el objeto de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::DestroyCtrl](../Topic/CMFCRibbonEdit::DestroyCtrl.md)|Destruye el objeto `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::DropDownList](../Topic/CMFCRibbonEdit::DropDownList.md)|Quita inactivo un cuadro de lista.|  
|[CMFCRibbonEdit::EnableSpinButtons](../Topic/CMFCRibbonEdit::EnableSpinButtons.md)|Permisos y establece el intervalo de botones de número para el cuadro de texto.|  
|[CMFCRibbonEdit::GetCompactSize](../Topic/CMFCRibbonEdit::GetCompactSize.md)|Recupera el tamaño compacto del objeto de `CFMCRibbonEdit` .|  
|[CMFCRibbonEdit::GetEditText](../Topic/CMFCRibbonEdit::GetEditText.md)|Recupera el texto del cuadro de texto.|  
|[CMFCRibbonEdit::GetIntermediateSize](../Topic/CMFCRibbonEdit::GetIntermediateSize.md)|Recupera el tamaño medio del objeto de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::GetTextAlign](../Topic/CMFCRibbonEdit::GetTextAlign.md)|Recupera la alineación del texto en el cuadro de texto.|  
|[CMFCRibbonEdit::GetWidth](../Topic/CMFCRibbonEdit::GetWidth.md)|Recupera el ancho, en píxeles, del control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::HasCompactMode](../Topic/CMFCRibbonEdit::HasCompactMode.md)|Indica si el tamaño de la presentación del control de `CMFCRibbonEdit` puede ser compacto.|  
|[CMFCRibbonEdit::HasFocus](../Topic/CMFCRibbonEdit::HasFocus.md)|Indica si el control de `CMFCRIbbonEdit` tiene el foco.|  
|[CMFCRibbonEdit::HasLargeMode](../Topic/CMFCRibbonEdit::HasLargeMode.md)|Indica si el tamaño de la presentación del control de `CMFCRibbonEdit` puede ser muy grande.|  
|[CMFCRibbonEdit::HasSpinButtons](../Topic/CMFCRibbonEdit::HasSpinButtons.md)|Indica si el cuadro de texto tiene un botón de número.|  
|[CMFCRibbonEdit::IsHighlighted](../Topic/CMFCRibbonEdit::IsHighlighted.md)|Indica si el control de `CMFCRibbonEdit` aparecerá resaltada.|  
|[CMFCRibbonEdit::OnAfterChangeRect](../Topic/CMFCRibbonEdit::OnAfterChangeRect.md)|Llamado por el marco cuando las dimensiones del rectángulo de presentación para los cambios de control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::OnDraw](../Topic/CMFCRibbonEdit::OnDraw.md)|Llamado por el marco para dibujar el control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](../Topic/CMFCRibbonEdit::OnDrawLabelAndImage.md)|Llamado por el marco para dibujar la etiqueta y la imagen para el control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::OnDrawOnList](../Topic/CMFCRibbonEdit::OnDrawOnList.md)|Llamado por el marco para dibujar el control de `CMFCRibbonEdit` en un cuadro de lista de comandos.|  
|[CMFCRibbonEdit::OnEnable](../Topic/CMFCRibbonEdit::OnEnable.md)|Llamado por el marco para habilitar o deshabilitar el control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::OnHighlight](../Topic/CMFCRibbonEdit::OnHighlight.md)|Llamado por el marco cuando el puntero entra o sale de los límites del control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::OnKey](../Topic/CMFCRibbonEdit::OnKey.md)|Llamado por el marco cuando el usuario presiona un keytip y el control de `CMFCRibbonEdit` tiene el foco.|  
|[CMFCRibbonEdit::OnLButtonDown](../Topic/CMFCRibbonEdit::OnLButtonDown.md)|Llamado por el marco para actualizar el control de `CMFCRibbonEdit` cuando el usuario presiona el botón primario en el control.|  
|[CMFCRibbonEdit::OnLButtonUp](../Topic/CMFCRibbonEdit::OnLButtonUp.md)|Llamado por el marco cuando el usuario suelta el botón primario.|  
|[CMFCRibbonEdit::OnRTLChanged](../Topic/CMFCRibbonEdit::OnRTLChanged.md)|Llamado por el marco para actualizar el control de `CMFCRibbonEdit` cuando el diseño cambia la dirección.|  
|[CMFCRibbonEdit::OnShow](../Topic/CMFCRibbonEdit::OnShow.md)|Llamado por el marco para mostrar u ocultar el control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::Redraw](../Topic/CMFCRibbonEdit::Redraw.md)|Actualiza la presentación del control de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::SetACCData](../Topic/CMFCRibbonEdit::SetACCData.md)|Establece los datos de accesibilidad para el objeto de `CMFCRibbonEdit` .|  
|[CMFCRibbonEdit::SetEditText](../Topic/CMFCRibbonEdit::SetEditText.md)|Establece el texto del cuadro de texto.|  
|[CMFCRibbonEdit::SetTextAlign](../Topic/CMFCRibbonEdit::SetTextAlign.md)|Establece la alineación del texto del cuadro de texto.|  
|[CMFCRibbonEdit::SetWidth](../Topic/CMFCRibbonEdit::SetWidth.md)|Establece el ancho del cuadro de texto del control de `CMFCRibbonEdit` .|  
  
## Comentarios  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCRibbonEdit` , muestra los botones de número junto al control de edición, y establece el texto del control de edición.  Este fragmento de código es parte de [Ejemplo 2007 de demostración de MS Office](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/CPP/cmfcribbonedit-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** afxRibbonEdit.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)