---
title: "CDragListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDragListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDragListBox class"
  - "drag list box [C++]"
  - "dragging list items"
  - "cuadros de lista"
  - "Windows [C++], cuadros de lista"
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CDragListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Además de proporcionar la funcionalidad de un cuadro de lista de Windows, la clase de `CDragListBox` permite al usuario mueva elementos de cuadro de lista, como nombres de archivo, en el cuadro de lista.  
  
## Sintaxis  
  
```  
class CDragListBox : public CListBox  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](../Topic/CDragListBox::CDragListBox.md)|Crea un objeto `CDragListBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](../Topic/CDragListBox::BeginDrag.md)|Llamado por el marco cuando una operación de arrastre inicia.|  
|[CDragListBox::CancelDrag](../Topic/CDragListBox::CancelDrag.md)|Llamado por el marco cuando una operación de arrastre se ha cancelado.|  
|[CDragListBox::Dragging](../Topic/CDragListBox::Dragging.md)|Llamado por el marco durante una operación de arrastre.|  
|[CDragListBox::DrawInsert](../Topic/CDragListBox::DrawInsert.md)|Dibuja la guía de inserción listbox de arrastre.|  
|[CDragListBox::Dropped](../Topic/CDragListBox::Dropped.md)|Llamado por el marco después de que se quite el elemento.|  
|[CDragListBox::ItemFromPt](../Topic/CDragListBox::ItemFromPt.md)|Devuelve las coordenadas del elemento que se arrastra.|  
  
## Comentarios  
 Los cuadros de lista con esta función permiten a los usuarios soliciten los elementos de una lista en cualquier forma le es más útil.  De forma predeterminada, el cuadro de lista mueva el elemento a la nueva ubicación en la lista.  Sin embargo, los objetos de `CDragListBox` se pueden personalizar para copiar elementos en lugar de moverlos.  
  
 El control de cuadro de lista asociada con la clase de `CDragListBox` no debe tener **LBS\_SORT** o el estilo de **LBS\_MULTIPLESELECT** .  Para obtener una descripción de los estilos del cuadro de lista, vea [Estilos de listbox](../../mfc/reference/list-box-styles.md).  
  
 Para usar un cuadro de lista de arrastre en un cuadro de diálogo existente de la aplicación, agregue un control de cuadro de lista con la plantilla de cuadro de diálogo mediante el editor de cuadros de diálogo y después asignar una variable miembro \(en la categoría `Control` y la variable escribe `CDragListBox`\) correspondiente al control de cuadro de lista de plantilla de cuadro de diálogo.  
  
 Para obtener más información sobre los controles a las variables miembro, vea [Acceso directo para las variables miembro de Definir para Controles de cuadro de diálogo](../../mfc/defining-member-variables-for-dialog-controls.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo TSTCON de MFC](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)