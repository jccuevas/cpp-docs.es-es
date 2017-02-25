---
title: "COleBusyDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleBusyDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleBusyDialog class"
  - "Server Busy dialog box"
  - "Server Not Responding dialog box"
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleBusyDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para los cuadros de diálogo ocupados de servidor OLE No Responder o Servidor.  
  
## Sintaxis  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](../Topic/COleBusyDialog::COleBusyDialog.md)|Crea un objeto `COleBusyDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](../Topic/COleBusyDialog::DoModal.md)|Muestra el cuadro de diálogo No disponible de servidor OLE.|  
|[COleBusyDialog::GetSelectionType](../Topic/COleBusyDialog::GetSelectionType.md)|Determina la elección realizada en el cuadro de diálogo.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleBusyDialog::m\_bz](../Topic/COleBusyDialog::m_bz.md)|Estructura de **OLEUIBUSY** tipo que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COleBusyDialog` cuando desea llamar a estos cuadros de diálogo.  Una vez construido un objeto de `COleBusyDialog` , puede utilizar la estructura de [m\_bz](../Topic/COleBusyDialog::m_bz.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_bz` es de **OLEUIBUSY**escrito.  Para obtener más información sobre cómo utilizar esta clase de cuadro de diálogo, vea la función miembro de [DoModal](../Topic/COleBusyDialog::DoModal.md) trabajar.  
  
> [!NOTE]
>  El código generado por aplicación contenedor utiliza esta clase.  
  
 Para obtener más información, vea la estructura de [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)