---
title: "COleLinksDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleLinksDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinksDialog class"
  - "cuadros de diálogo, OLE"
  - "Edit Links dialog box"
  - "OLE Edit Links dialog box"
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleLinksDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para edición\) enlaza el cuadro de diálogo.  
  
## Sintaxis  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](../Topic/COleLinksDialog::COleLinksDialog.md)|Crea un objeto `COleLinksDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](../Topic/COleLinksDialog::DoModal.md)|Muestra el cuadro de diálogo OLE de los vínculos de edición.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleLinksDialog::m\_el](../Topic/COleLinksDialog::m_el.md)|Una estructura de **OLEUIEDITLINKS** tipo que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COleLinksDialog` cuando desea llamar este cuadro de diálogo.  Una vez construido un objeto de `COleLinksDialog` , puede utilizar la estructura de [m\_el](../Topic/COleLinksDialog::m_el.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_el` es de **OLEUIEDITLINKS**escrito.  Para obtener más información sobre cómo utilizar esta clase de cuadro de diálogo, vea la función miembro de [DoModal](../Topic/COleLinksDialog::DoModal.md) trabajar.  
  
> [!NOTE]
>  El código generado por aplicación contenedor utiliza esta clase.  
  
 Para obtener más información, vea la estructura de [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)