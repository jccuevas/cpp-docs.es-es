---
title: "CMFCImageEditorDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImageEditorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImageEditorDialog class"
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMFCImageEditorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCImageEditorDialog` admite un cuadro de diálogo del editor de imágenes.  
  
## Sintaxis  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](../Topic/CMFCImageEditorDialog::CMFCImageEditorDialog.md)|Crea un objeto `CMFCImageEditorDialog`.|  
  
## Comentarios  
 La clase de `CMFCImageEditorDialog` proporciona un cuadro de diálogo que incluye:  
  
-   Un área de imagen que se utiliza para modificar los píxeles individuales de una imagen.  
  
-   Herramientas de dibujo para modificar los píxeles del área de imagen.  
  
-   Una paleta de colores para especificar el color utilizada por las herramientas de dibujo.  
  
-   Un área de vista previa que muestra el efecto de edición.  
  
 La ilustración siguiente muestra un cuadro de diálogo del editor de imágenes.  
  
 ![Cuadro de diálogo CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "ImageEdit")  
  
 Una manera de utilizar un objeto de `CMFCImageEditorDialog` es pasarlo una imagen de `CBitmap` que se editan.  No cree una imagen grande porque el área de edición de imagen tiene un tamaño limitado y el tamaño lógico de píxeles se ajusta para ajustarse al área.  Llame al método de `DoModal` para iniciar un cuadro de diálogo modal.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## Requisitos  
 **encabezado:** afximageeditordialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)