---
title: "COleUpdateDialog Class | Microsoft Docs"
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
  - "COleUpdateDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleUpdateDialog class"
  - "vínculos [C++], actualizar"
  - "cuadros de diálogo de OLE, Edit Link"
  - "OLE link updating"
  - "Update dialog"
  - "updating OLE links"
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleUpdateDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para un caso especial de edición\) enlaza el cuadro de diálogo, que se debe utilizar cuando necesite actualizar sólo objetos vinculados o incrustados existentes en un documento.  
  
## Sintaxis  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](../Topic/COleUpdateDialog::COleUpdateDialog.md)|Crea un objeto `COleUpdateDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](../Topic/COleUpdateDialog::DoModal.md)|Muestra el cuadro de diálogo de **Vínculos de edición** en un modo de actualización.|  
  
## Comentarios  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [COleLinksDialog Class](../../mfc/reference/colelinksdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog Class](../../mfc/reference/colelinksdialog-class.md)