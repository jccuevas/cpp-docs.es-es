---
title: "CDialogEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogEx class"
  - "CDialogEx::PreTranslateMessage method"
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CDialogEx` especifica el color de fondo y la imagen de fondo de un cuadro de diálogo.  
  
## Sintaxis  
  
```  
class CDialogEx : public CDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogEx::CDialogEx](../Topic/CDialogEx::CDialogEx.md)|Construye un objeto `CDialogEx`.|  
|`CDialogEx::~CDialogEx`|Destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDialogEx::SetBackgroundColor](../Topic/CDialogEx::SetBackgroundColor.md)|Establece el color de fondo del cuadro de diálogo.|  
|[CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md)|Establece la imagen de fondo del cuadro de diálogo.|  
  
## Comentarios  
 Para usar la clase `CDialogEx`, derive la clase de cuadro de diálogo de la clase `CDialogEx`, en lugar de derivarla de la clase `CDialog`.  
  
 Las imágenes del cuadro de diálogo se almacenan en un archivo de recursos.  El marco de trabajo elimina automáticamente cualquier imagen que se cargue desde el archivo de recursos.  Para eliminar mediante programación la imagen de fondo actual, llame al método [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md) o implemente un controlador de eventos `OnDestroy`.  Al llamar al método [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md), pase un parámetro `HBITMAP` como identificador de la imagen.  El objeto `CDialogEx` tomará posesión de la imagen y la elimina si la marca `m_bAutoDestroyBmp` es `TRUE`.  
  
 Un objeto `CDialogEx` puede ser un elemento primario de un objeto [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md).  El objeto [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) llama al método `CDialogEx::SetActiveMenu` cuando se abre el objeto [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md).  A continuación, el objeto `CDialogEx` controla cualquier evento de menú hasta que se cierre el objeto [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## Requisitos  
 **Encabezado:** afxdialogex.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)