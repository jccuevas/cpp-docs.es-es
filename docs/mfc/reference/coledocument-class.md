---
title: "COleDocument Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocument class"
  - "documentos, OLE"
  - "OLE containers, client items"
  - "OLE documents"
  - "OLE documents, clase base"
  - "visual editing, OLE document base class"
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la clase base para los documentos de OLE que admiten la edición visual.  
  
## Sintaxis  
  
```  
class COleDocument : public CDocument  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::COleDocument](../Topic/COleDocument::COleDocument.md)|Crea un objeto `COleDocument`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::AddItem](../Topic/COleDocument::AddItem.md)|agrega un elemento a la lista de elementos mantenidos por el documento.|  
|[COleDocument::ApplyPrintDevice](../Topic/COleDocument::ApplyPrintDevice.md)|Establece el dispositivo de IMPR\-destino para todos los elementos de cliente en el documento.|  
|[COleDocument::EnableCompoundFile](../Topic/COleDocument::EnableCompoundFile.md)|Documentos de las causas que se almacenarán en formato de archivo OLE de almacenamiento estructurado.|  
|[COleDocument::GetInPlaceActiveItem](../Topic/COleDocument::GetInPlaceActiveItem.md)|Devuelve el elemento OLE que está actualmente activo en contexto.|  
|[COleDocument::GetNextClientItem](../Topic/COleDocument::GetNextClientItem.md)|Obtiene el siguiente elemento de cliente para recorrer.|  
|[COleDocument::GetNextItem](../Topic/COleDocument::GetNextItem.md)|Obtiene el siguiente elemento de documento para recorrer.|  
|[COleDocument::GetNextServerItem](../Topic/COleDocument::GetNextServerItem.md)|Obtiene el elemento siguiente del servidor para recorrer.|  
|[COleDocument::GetPrimarySelectedItem](../Topic/COleDocument::GetPrimarySelectedItem.md)|Devuelve el elemento OLE seleccionado primario en el documento.|  
|[COleDocument::GetStartPosition](../Topic/COleDocument::GetStartPosition.md)|Obtiene la posición inicial para iniciar iteración.|  
|[COleDocument::HasBlankItems](../Topic/COleDocument::HasBlankItems.md)|Busca elementos en blanco en el documento.|  
|[COleDocument::OnShowViews](../Topic/COleDocument::OnShowViews.md)|Se llama cuando el documento se vuelve visible o invisible.|  
|[COleDocument::RemoveItem](../Topic/COleDocument::RemoveItem.md)|quita un elemento de la lista de elementos mantenidos por el documento.|  
|[COleDocument::UpdateModifiedFlag](../Topic/COleDocument::UpdateModifiedFlag.md)|Marca el documento como modificado si se han modificado los elementos de OLE contenido cualquiera de los.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](../Topic/COleDocument::OnEditChangeIcon.md)|Controla eventos en el comando del menú de icono de cambio.|  
|[COleDocument::OnEditConvert](../Topic/COleDocument::OnEditConvert.md)|Controla la conversión de un incrustado o el objeto vinculado a partir de un tipo a otro.|  
|[COleDocument::OnEditLinks](../Topic/COleDocument::OnEditLinks.md)|Controla eventos en el comando de los vínculos en el menú Edición.|  
|[COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)|Envía un mensaje de correo con el documento asociado.|  
|[COleDocument::OnUpdateEditChangeIcon](../Topic/COleDocument::OnUpdateEditChangeIcon.md)|Llamado por el marco para actualizar la interfaz de usuario de comandos para la opción de menú del icono de edición y de cambio.|  
|[COleDocument::OnUpdateEditLinksMenu](../Topic/COleDocument::OnUpdateEditLinksMenu.md)|Llamado por el marco para actualizar la interfaz de usuario de comandos para la opción de menú de edición y de los vínculos.|  
|[COleDocument::OnUpdateObjectVerbMenu](../Topic/COleDocument::OnUpdateObjectVerbMenu.md)|Llamado por el marco para actualizar la interfaz de usuario de comandos para la opción de menú de edición y*de ObjectName* y el submenú de verbo acceso de edición y*de ObjectName*.|  
|[COleDocument::OnUpdatePasteLinkMenu](../Topic/COleDocument::OnUpdatePasteLinkMenu.md)|Llamado por el marco para actualizar la interfaz de usuario de comandos para la opción de menú de pegar especial.|  
|[COleDocument::OnUpdatePasteMenu](../Topic/COleDocument::OnUpdatePasteMenu.md)|Llamado por el marco para actualizar la interfaz de usuario de comandos para la opción de menú pegar.|  
  
## Comentarios  
 `COleDocument` es derivado de **CDocument**, que permite que las aplicaciones OLE para utilizar la arquitectura documento\/vista proporcionada por la biblioteca Microsoft Foundation Class.  
  
 `COleDocument` trata un documento como una colección de objetos de [CDocItem](../../mfc/reference/cdocitem-class.md) administrar elementos de OLE.  El contenedor y las aplicaciones de servidor requiere esta arquitectura porque los documentos pueden contener elementos de OLE.  las clases de [COleServerItem](../../mfc/reference/coleserveritem-class.md) y de [COleClientItem](../../mfc/reference/coleclientitem-class.md) , derivadas de `CDocItem`, administran las interacciones entre las aplicaciones y los elementos de OLE.  
  
 Si está escribiendo una aplicación contenedora simple, derive la clase de `COleDocument`.  Si está escribiendo una aplicación contenedora que admita vincular elementos incrustados contenidos en los documentos, derive la clase de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md).  Si está escribiendo un contenedor de la aplicación de servidor o de combinación y el servidor, derive la clase de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md).  `COleLinkingDoc` y `COleServerDoc` son derivados de `COleDocument`, por lo que estas clases heredan todos los servicios disponibles en `COleDocument` y **CDocument**.  
  
 Para utilizar `COleDocument`, derive una clase de ella y agregar funcionalidad para administrar los datos de no\-OLE de la aplicación así como elementos insertados o vinculados.  Si define `CDocItem`\- clases derivadas para almacenar datos nativos de la aplicación, puede utilizar la implementación predeterminada definida por `COleDocument` para almacenar los datos de OLE y de no\-OLE.  También puede diseñar dispone de las estructuras de datos para almacenar los datos de no\-OLE por separado de los elementos de OLE.  Para obtener más información, vea el artículo [contenedores: archivos compuestos](../../mfc/containers-compound-files.md).  
  
 **CDocument** admite el envío del documento mediante correo si la compatibilidad de correo \(MAPI\) está presente.  `COleDocument` ha actualizado [OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md) para administrar documentos compuestos correctamente.  Para obtener más información, vea los artículos [MAPI](../../mfc/mapi.md) y [Compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [CONTAINER de ejemplo de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo MFCBIND de MFC](../../top/visual-cpp-samples.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)