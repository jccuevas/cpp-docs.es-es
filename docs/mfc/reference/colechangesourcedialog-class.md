---
title: "COleChangeSourceDialog Class | Microsoft Docs"
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
  - "COleChangeSourceDialog"
  - "OLEUICHANGESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleChangeSourceDialog class"
  - "cuadros de diálogo, OLE"
  - "OLE Change Source dialog box"
  - "cuadros de diálogo de OLE, Change Source"
  - "OleUIChangeSource structure"
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleChangeSourceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado para el cuadro de diálogo Y el origen del cambio.  
  
## Sintaxis  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](../Topic/COleChangeSourceDialog::COleChangeSourceDialog.md)|Crea un objeto `COleChangeSourceDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeSourceDialog::DoModal](../Topic/COleChangeSourceDialog::DoModal.md)|Muestra el cuadro de diálogo Y el origen del cambio.|  
|[COleChangeSourceDialog::GetDisplayName](../Topic/COleChangeSourceDialog::GetDisplayName.md)|Obtiene el nombre para mostrar de origen completo.|  
|[COleChangeSourceDialog::GetFileName](../Topic/COleChangeSourceDialog::GetFileName.md)|Obtiene el nombre de archivo del nombre de origen.|  
|[COleChangeSourceDialog::GetFromPrefix](../Topic/COleChangeSourceDialog::GetFromPrefix.md)|Obtiene el prefijo de origen anterior.|  
|[COleChangeSourceDialog::GetItemName](../Topic/COleChangeSourceDialog::GetItemName.md)|Obtiene el nombre de elemento name de origen.|  
|[COleChangeSourceDialog::GetToPrefix](../Topic/COleChangeSourceDialog::GetToPrefix.md)|Obtiene el prefijo de nuevo origen|  
|[COleChangeSourceDialog::IsValidSource](../Topic/COleChangeSourceDialog::IsValidSource.md)|indica si el origen es válido.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleChangeSourceDialog::m\_cs](../Topic/COleChangeSourceDialog::m_cs.md)|Una estructura que controla el comportamiento del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COleChangeSourceDialog` cuando desea llamar este cuadro de diálogo.  Una vez construido un objeto de `COleChangeSourceDialog` , puede utilizar la estructura de [m\_cs](../Topic/COleChangeSourceDialog::m_cs.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_cs` es de [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)escrito.  Para obtener más información sobre cómo utilizar esta clase de cuadro de diálogo, vea la función miembro de [DoModal](../Topic/COleChangeSourceDialog::DoModal.md) trabajar.  
  
 Para obtener más información, vea la estructura de [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)