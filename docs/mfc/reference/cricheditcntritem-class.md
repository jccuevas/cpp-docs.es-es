---
title: "CRichEditCntrItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditCntrItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCntrItem class"
  - "OLE items, in rich edit views"
  - "controles Rich Edit, OLE items"
  - "controles Rich Edit, utilizar"
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRichEditCntrItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditCntrItem::CRichEditCntrItem](../Topic/CRichEditCntrItem::CRichEditCntrItem.md)|Crea un objeto `CRichEditCntrItem`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditCntrItem::SyncToRichEditObject](../Topic/CRichEditCntrItem::SyncToRichEditObject.md)|Genera el elemento como otro tipo.|  
  
## Comentarios  
 Un “control rich edit” es una ventana en la que el usuario puede escribir y modificar texto.  el texto se puede asignar el carácter y el formato de párrafo, y puede incluir objetos OLE incrustados.  Los controles rich edit proporcionan una interfaz de programación para dar formato al texto.  Sin embargo, una aplicación debe implementar cualquier componente de la interfaz de usuario necesario colocar operaciones de formato a disposición del usuario.  
  
 `CRichEditView` mantiene el texto y la característica de formato de texto.  `CRichEditDoc` mantiene la lista de elementos de OLE de cliente que están en la vista.  `CRichEditCntrItem` proporciona acceso de contenedor\-lado el elemento OLE de cliente.  
  
 Este control común de Windows \(y por consiguiente [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas\) sólo está disponible para los programas que se ejecutan en versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  
  
 Para obtener un ejemplo de enriquecido mediante editar los elementos del contenedor en una aplicación MFC, vea la aplicación de ejemplo de [WORDPAD](../../top/visual-cpp-samples.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## Requisitos  
 **encabezado:** afxrich.h  
  
## Vea también  
 [ejemplo WORDPAD de MFC](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)