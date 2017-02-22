---
title: "COleConvertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleConvertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleConvertDialog class"
  - "Convertir (cuadro de diálogo)"
  - "cuadros de diálogo, OLE"
  - "OLE Convert dialog box"
  - "cuadros de diálogo de OLE, Convert"
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleConvertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para obtener más información, vea la estructura de [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Sintaxis  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](../Topic/COleConvertDialog::COleConvertDialog.md)|Crea un objeto `COleConvertDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](../Topic/COleConvertDialog::DoConvert.md)|Realiza la conversión especificada en el cuadro de diálogo.|  
|[COleConvertDialog::DoModal](../Topic/COleConvertDialog::DoModal.md)|Muestra el cuadro de diálogo OLE del elemento de cambio.|  
|[COleConvertDialog::GetClassID](../Topic/COleConvertDialog::GetClassID.md)|Obtiene **Id. de clase** asociado al elemento elegido.|  
|[COleConvertDialog::GetDrawAspect](../Topic/COleConvertDialog::GetDrawAspect.md)|Especifica si dibujar el elemento como un icono.|  
|[COleConvertDialog::GetIconicMetafile](../Topic/COleConvertDialog::GetIconicMetafile.md)|Obtiene un identificador al metarchivo asociado al formulario icónico de este elemento.|  
|[COleConvertDialog::GetSelectionType](../Topic/COleConvertDialog::GetSelectionType.md)|obtiene el tipo de selección elegido.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleConvertDialog::m\_cv](../Topic/COleConvertDialog::m_cv.md)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
  
> [!NOTE]
>  El código generado por aplicación contenedor utiliza esta clase.  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)