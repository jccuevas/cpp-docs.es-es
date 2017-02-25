---
title: "CRichEditDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditDoc class"
  - "document/view architecture, controles Rich Edit"
  - "documentos, rich edit"
  - "OLE containers, rich edit"
  - "controles Rich Edit, OLE container"
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRichEditDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
  
class CRichEditDoc : public COleServerDoc  
  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](../Topic/CRichEditDoc::CreateClientItem.md)|Denominado para realizar la limpieza del documento.|  
|[CRichEditDoc::GetStreamFormat](../Topic/CRichEditDoc::GetStreamFormat.md)|Indica si la entrada y la secuencia deben incluir información de formato.|  
|[CRichEditDoc::GetView](../Topic/CRichEditDoc::GetView.md)|recupera el objeto asssociated de [CRichEditView](../../mfc/reference/cricheditview-class.md) .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditDoc::m\_bRTF](../Topic/CRichEditDoc::m_bRTF.md)|indica si la E\/S de secuencia debe incluir el formato.|  
  
## Comentarios  
 Un “control rich edit” es una ventana en la que el usuario puede escribir y modificar texto.  el texto se puede asignar el carácter y el formato de párrafo, y puede incluir objetos OLE incrustados.  Los controles rich edit proporcionan una interfaz de programación para dar formato al texto.  Sin embargo, una aplicación debe implementar cualquier componente de la interfaz de usuario necesario colocar operaciones de formato a disposición del usuario.  
  
 `CRichEditView` mantiene el texto y la característica de formato de texto.  `CRichEditDoc` mantiene la lista de elementos de cliente que están en la vista.  `CRichEditCntrItem` proporciona acceso de contenedor\-lado a los elementos de OLE de cliente.  
  
 Este control común de Windows \(y por consiguiente [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas\) sólo está disponible para los programas que se ejecutan en versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  
  
 Para obtener un ejemplo de cómo utilizar un documento completo de edición en una aplicación MFC, vea la aplicación de ejemplo de [WORDPAD](../../top/visual-cpp-samples.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## Requisitos  
 **encabezado:** afxrich.h  
  
## Vea también  
 [ejemplo WORDPAD de MFC](../../top/visual-cpp-samples.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl Class](../../mfc/reference/cricheditctrl-class.md)