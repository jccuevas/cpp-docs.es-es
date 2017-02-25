---
title: "COleDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDialog class"
  - "cuadros de diálogo, OLE"
  - "cuadros de diálogo de OLE, clase base"
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona funcionalidad común a los cuadros de diálogo para OLE.  
  
## Sintaxis  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDialog::GetLastError](../Topic/COleDialog::GetLastError.md)|obtiene el código de error devuelto por el cuadro de diálogo.|  
  
## Comentarios  
 La biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `COleDialog`:  
  
-   [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
-   [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
-   [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
-   [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
-   [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
-   [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
-   [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
-   [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
-   [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)