---
title: "COleChangeIconDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleChangeIconDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Change Icon dialog box"
  - "COleChangeIconDialog class"
  - "cuadros de diálogo, OLE"
  - "OLE Change Icon dialog box"
  - "cuadros de diálogo de OLE, Change Icon"
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleChangeIconDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado para el cuadro de diálogo OLE de icono de cambio.  
  
## Sintaxis  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](../Topic/COleChangeIconDialog::COleChangeIconDialog.md)|Crea un objeto `COleChangeIconDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](../Topic/COleChangeIconDialog::DoChangeIcon.md)|Realiza el cambio especificado en el cuadro de diálogo.|  
|[COleChangeIconDialog::DoModal](../Topic/COleChangeIconDialog::DoModal.md)|Muestra el cuadro de diálogo del icono de cambio OLE 2.|  
|[COleChangeIconDialog::GetIconicMetafile](../Topic/COleChangeIconDialog::GetIconicMetafile.md)|Obtiene un identificador al metarchivo asociado al formulario icónico de este elemento.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeIconDialog::m\_ci](../Topic/COleChangeIconDialog::m_ci.md)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COleChangeIconDialog` cuando desea llamar este cuadro de diálogo.  Una vez construido un objeto de `COleChangeIconDialog` , puede utilizar la estructura de [m\_ci](../Topic/COleChangeIconDialog::m_ci.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_ci` es de **OLEUICHANGEICON**escrito.  Para obtener más información sobre cómo utilizar esta clase de cuadro de diálogo, vea la función miembro de [DoModal](../Topic/COleChangeIconDialog::DoModal.md) trabajar.  
  
 Para obtener más información, vea la estructura de [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)