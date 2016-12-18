---
title: "COlePasteSpecialDialog Class | Microsoft Docs"
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
  - "COlePasteSpecialDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePasteSpecialDialog class"
  - "cuadros de diálogo, Paste Special"
  - "OLE Paste Special dialog box"
  - "Paste Special dialog box"
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COlePasteSpecialDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado para el cuadro de diálogo OLE de pegar especial.  
  
## Sintaxis  
  
```  
  
class COlePasteSpecialDialog : public COleDialog  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](../Topic/COlePasteSpecialDialog::COlePasteSpecialDialog.md)|Crea un objeto `COlePasteSpecialDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md)|Agrega formatos personalizados a la lista de formatos que la aplicación puede pegar.|  
|[COlePasteSpecialDialog::AddLinkEntry](../Topic/COlePasteSpecialDialog::AddLinkEntry.md)|Agrega una nueva entrada a la lista de formatos de Portapapeles admitidos.|  
|[COlePasteSpecialDialog::AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md)|Agrega **CF\_BITMAP**, **CF\_DIB**, `CF_METAFILEPICT`y, opcionalmente `CF_LINKSOURCE` a la lista de formatos que la aplicación puede pegar.|  
|[COlePasteSpecialDialog::CreateItem](../Topic/COlePasteSpecialDialog::CreateItem.md)|Crea el elemento en el documento contenedor utilizando el formato especificado.|  
|[COlePasteSpecialDialog::DoModal](../Topic/COlePasteSpecialDialog::DoModal.md)|Muestra el cuadro de diálogo de OLE Paste Special.|  
|[COlePasteSpecialDialog::GetDrawAspect](../Topic/COlePasteSpecialDialog::GetDrawAspect.md)|Indica si dibujar el elemento como un icono o no.|  
|[COlePasteSpecialDialog::GetIconicMetafile](../Topic/COlePasteSpecialDialog::GetIconicMetafile.md)|Obtiene un identificador al metarchivo asociado al formulario icónico de este elemento.|  
|[COlePasteSpecialDialog::GetPasteIndex](../Topic/COlePasteSpecialDialog::GetPasteIndex.md)|Obtiene el índice de opciones de pegar disponibles que ha elegido por el usuario.|  
|[COlePasteSpecialDialog::GetSelectionType](../Topic/COlePasteSpecialDialog::GetSelectionType.md)|obtiene el tipo de selección elegido.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md)|Una estructura de **OLEUIPASTESPECIAL** tipo que controla la función del cuadro de diálogo.|  
  
## Comentarios  
 Cree un objeto de clase `COlePasteSpecialDialog` cuando desea llamar este cuadro de diálogo.  Una vez construido un objeto de `COlePasteSpecialDialog` , puede utilizar [AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md) y el miembro de [AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md) funciona para agregar formatos del Portapapeles en el cuadro de diálogo.  También puede utilizar la estructura de [m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md) para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de `m_ps` es de **OLEUIPASTESPECIAL**escrito.  
  
 Para obtener más información, vea la estructura de [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre los cuadros de diálogo OLE\-específicos, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)