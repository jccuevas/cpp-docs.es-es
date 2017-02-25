---
title: "COleDocObjectItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDocObjectItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocObjectItem class"
  - "containment"
  - "containment, doc object"
  - "doc object containment"
  - "document object containment"
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleDocObjectItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la contención del documento activo.  
  
## Sintaxis  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](../Topic/COleDocObjectItem::COleDocObjectItem.md)|Crea un elemento de `COleDocObject` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](../Topic/COleDocObjectItem::DoDefaultPrinting.md)|Imprime el documento de la aplicación contenedora mediante una configuración de impresora predeterminada.|  
|[COleDocObjectItem::ExecCommand](../Topic/COleDocObjectItem::ExecCommand.md)|ejecuta el comando especificado por el usuario.|  
|[COleDocObjectItem::GetActiveView](../Topic/COleDocObjectItem::GetActiveView.md)|Recupera la vista activa del documento.|  
|[COleDocObjectItem::GetPageCount](../Topic/COleDocObjectItem::GetPageCount.md)|recupera el número de páginas en el documento de la aplicación contenedora.|  
|[COleDocObjectItem::OnPreparePrinting](../Topic/COleDocObjectItem::OnPreparePrinting.md)|Prepara el documento de la aplicación contenedora para imprimir.|  
|[COleDocObjectItem::OnPrint](../Topic/COleDocObjectItem::OnPrint.md)|imprime el documento de la aplicación contenedora.|  
|[COleDocObjectItem::QueryCommand](../Topic/COleDocObjectItem::QueryCommand.md)|Consultas para el estado de uno o más comandos generados por eventos de interfaz de usuario.|  
|[COleDocObjectItem::Release](../Topic/COleDocObjectItem::Release.md)|Libera la conexión OLE vincularon el elemento y cierre él si estaba abierto.  No destruye el elemento customer.|  
  
## Comentarios  
 En MFC, un documento activo se controla de forma similar a un archivo, incrustación modificable en contexto, con las siguientes diferencias:  
  
-   `COleDocument`\- clase derivada mantiene una lista de los elementos incrustados actualmente; sin embargo, estos elementos pueden ser `COleDocObjectItem`\- elementos derivados.  
  
-   Cuando un documento activo está activo, ocupa toda el área de cliente de la vista cuando está activo en contexto.  
  
-   Un contenedor de documentos activos tiene control completo del menú de **Ayuda** .  
  
-   El menú de **Ayuda** contiene elementos de menú para el contenedor y el servidor de documentos activos.  
  
 Puesto que el contenedor de documentos activos posee el menú de **Ayuda** , el contenedor es responsable de reenviar mensajes de menú de **Ayuda** de servidor al servidor.  Esta integración controla `COleDocObjectItem`.  
  
 Para obtener más información sobre la combinación de menús y la activación del documento activo, vea información general de [Contención de documento activo](../../mfc/active-document-containment.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo MFCBIND de MFC](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)