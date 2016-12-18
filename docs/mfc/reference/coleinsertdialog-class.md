---
title: "COleInsertDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleInsertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleInsertDialog class"
  - "cuadros de diálogo, OLE"
  - "Insert Object dialog box"
  - "OLE Insert Object dialog box"
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleInsertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado para el cuadro de diálogo OLE de objeto INSERT.  
  
## Sintaxis  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](../Topic/COleInsertDialog::COleInsertDialog.md)|Crea un objeto `COleInsertDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](../Topic/COleInsertDialog::CreateItem.md)|crea el elemento seleccionado en el cuadro de diálogo.|  
|[COleInsertDialog::DoModal](../Topic/COleInsertDialog::DoModal.md)|Muestra el cuadro de diálogo OLE de objeto INSERT.|  
|[COleInsertDialog::GetClassID](../Topic/COleInsertDialog::GetClassID.md)|Obtiene **Id. de clase** asociado al elemento elegido.|  
|[COleInsertDialog::GetDrawAspect](../Topic/COleInsertDialog::GetDrawAspect.md)|Indica si dibujar el elemento como un icono.|  
|[COleInsertDialog::GetIconicMetafile](../Topic/COleInsertDialog::GetIconicMetafile.md)|Obtiene un identificador al metarchivo asociado al formulario icónico de este elemento.|  
|[COleInsertDialog::GetPathName](../Topic/COleInsertDialog::GetPathName.md)|Obtiene la ruta de acceso completa al archivo elegido en el cuadro de diálogo.|  
|[COleInsertDialog::GetSelectionType](../Topic/COleInsertDialog::GetSelectionType.md)|obtiene el tipo de objeto seleccionado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleInsertDialog::m\_io](../Topic/COleInsertDialog::m_io.md)|Una estructura de **OLEUIINSERTOBJECT** tipo que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COleInsertDialog` cuando desea llamar este cuadro de diálogo.  Una vez construido un objeto de `COleInsertDialog` , puede utilizar la estructura de [m\_io](../Topic/COleInsertDialog::m_io.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_io` es de **OLEUIINSERTOBJECT**escrito.  Para obtener más información sobre cómo utilizar esta clase de cuadro de diálogo, vea la función miembro de [DoModal](../Topic/COleInsertDialog::DoModal.md) trabajar.  
  
> [!NOTE]
>  El código generado por aplicación contenedor utiliza esta clase.  
  
 Para obtener más información, vea la estructura de [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)