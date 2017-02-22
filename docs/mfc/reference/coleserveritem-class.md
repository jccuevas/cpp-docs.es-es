---
title: "COleServerItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerItem class"
  - "aplicaciones de servidor OLE, managing server documents"
  - "aplicaciones de servidor OLE, server interfaces"
  - "OLE server documents"
  - "servidores, OLE"
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la interfaz del servidor a los elementos de OLE.  
  
## Sintaxis  
  
```  
class COleServerItem : public CDocItem  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::COleServerItem](../Topic/COleServerItem::COleServerItem.md)|Crea un objeto `COleServerItem`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](../Topic/COleServerItem::AddOtherClipboardData.md)|Formatos de presentación y la conversión de los lugares de un objeto de `COleDataSource` .|  
|[COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md)|Copia el elemento en el portapapeles.|  
|[COleServerItem::DoDragDrop](../Topic/COleServerItem::DoDragDrop.md)|Realiza una operación de arrastrar y colocar.|  
|[COleServerItem::GetClipboardData](../Topic/COleServerItem::GetClipboardData.md)|Obtiene el origen de datos para su uso en la transferencia de datos \(arrastrar y colocar o portapapeles\).|  
|[COleServerItem::GetDocument](../Topic/COleServerItem::GetDocument.md)|Devuelve el documento del servidor que contiene el elemento.|  
|[COleServerItem::GetEmbedSourceData](../Topic/COleServerItem::GetEmbedSourceData.md)|Obtiene los datos de **CF\_EMBEDSOURCE** para un elemento.|  
|[COleServerItem::GetItemName](../Topic/COleServerItem::GetItemName.md)|Devuelve el nombre del elemento.  Se usa para los elementos vinculados sólo.|  
|[COleServerItem::GetLinkSourceData](../Topic/COleServerItem::GetLinkSourceData.md)|Obtiene los datos de `CF_LINKSOURCE` para un elemento.|  
|[COleServerItem::GetObjectDescriptorData](../Topic/COleServerItem::GetObjectDescriptorData.md)|Obtiene los datos de **CF\_OBJECTDESCRIPTOR** para un elemento.|  
|[COleServerItem::IsConnected](../Topic/COleServerItem::IsConnected.md)|Indica si el elemento está asociado actualmente a un contenedor activo.|  
|[COleServerItem::IsLinkedItem](../Topic/COleServerItem::IsLinkedItem.md)|Indica si el elemento representa un elemento OLE vinculado.|  
|[COleServerItem::NotifyChanged](../Topic/COleServerItem::NotifyChanged.md)|Actualiza todos los contenedores con actualización de vínculo automático.|  
|[COleServerItem::OnDoVerb](../Topic/COleServerItem::OnDoVerb.md)|denominado para ejecutar un verbo.|  
|[COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)|Se invoca cuando las solicitudes de contenedor para dibujar el elemento; implementación necesaria.|  
|[COleServerItem::OnDrawEx](../Topic/COleServerItem::OnDrawEx.md)|Denominado para el gráfico especializado del elemento.|  
|[COleServerItem::OnGetClipboardData](../Topic/COleServerItem::OnGetClipboardData.md)|Llamado por el marco para obtener los datos que se copian en el portapapeles.|  
|[COleServerItem::OnGetExtent](../Topic/COleServerItem::OnGetExtent.md)|Llamado por el marco para recuperar el tamaño del elemento.|  
|[COleServerItem::OnInitFromData](../Topic/COleServerItem::OnInitFromData.md)|Llamado por el marco para inicializar un elemento OLE mediante el contenido del objeto de transferencia de datos especificado.|  
|[COleServerItem::OnQueryUpdateItems](../Topic/COleServerItem::OnQueryUpdateItems.md)|denominado para determinar si algunos elementos vinculados requieren actualizar.|  
|[COleServerItem::OnRenderData](../Topic/COleServerItem::OnRenderData.md)|Recupera los datos como parte de generar retrasada.|  
|[COleServerItem::OnRenderFileData](../Topic/COleServerItem::OnRenderFileData.md)|Recupera datos de un objeto de `CFile` como parte de generar retrasada.|  
|[COleServerItem::OnRenderGlobalData](../Topic/COleServerItem::OnRenderGlobalData.md)|Recupera datos de `HGLOBAL` como parte de generar retrasada.|  
|[COleServerItem::OnSetColorScheme](../Topic/COleServerItem::OnSetColorScheme.md)|Denominado para establecer la combinación de colores del elemento.|  
|[COleServerItem::OnSetData](../Topic/COleServerItem::OnSetData.md)|Denominado para establecer los datos de elemento.|  
|[COleServerItem::OnSetExtent](../Topic/COleServerItem::OnSetExtent.md)|Llamado por el marco para establecer el tamaño del elemento.|  
|[COleServerItem::OnUpdate](../Topic/COleServerItem::OnUpdate.md)|Se invoca cuando pertenece un poco del documento el elemento en cambia.|  
|[COleServerItem::OnUpdateItems](../Topic/COleServerItem::OnUpdateItems.md)|Denominado para actualizar la memoria caché de todos los elementos del documento del servidor.|  
|[COleServerItem::SetItemName](../Topic/COleServerItem::SetItemName.md)|Establece el nombre del elemento.  Se usa para los elementos vinculados sólo.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](../Topic/COleServerItem::GetDataSource.md)|Obtiene el objeto utilizado a formatos almacenados de conversión.|  
|[COleServerItem::OnHide](../Topic/COleServerItem::OnHide.md)|Llamado por el marco para ocultar el elemento.|  
|[COleServerItem::OnOpen](../Topic/COleServerItem::OnOpen.md)|Llamado por el marco para mostrar el elemento OLE en su propia ventana de nivel superior.|  
|[COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md)|Se invoca cuando las solicitudes de contenedor para mostrar el elemento.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::m\_sizeExtent](../Topic/COleServerItem::m_sizeExtent.md)|Informa al servidor sobre cuánto de elemento OLE está visible.|  
  
## Comentarios  
 Un elemento vinculado puede representar parte o todo el documento del servidor.  Un elemento incrustado siempre representa un documento completo del servidor.  
  
 La clase de `COleServerItem` define varias funciones overridable miembro que son llamadas por las bibliotecas de vínculos dinámicos del sistema OLE \(DLLs\), normalmente en respuesta a las solicitudes de la aplicación contenedora.  Estas funciones miembro permiten la aplicación contenedora para manipular el elemento indirectamente de varias maneras, por ejemplo mostrarla, ejecutar los verbos, o recuperar los datos en diferentes formatos.  
  
 Para utilizar `COleServerItem`, derive una clase de ella y implementar el miembro de [OnDraw](../Topic/COleServerItem::OnDraw.md) y de [serialice](../Topic/CObject::Serialize.md) funciona.  La función de `OnDraw` proporciona la representación de metarchivo de un elemento, lo que se mostrará cuando abra una aplicación contenedora un documento compuesto.  La función de `Serialize` de `CObject` proporciona la representación nativa de un elemento, permitiendo que un elemento incrustado se transfieren entre el servidor y las aplicaciones contenedoras.  [OnGetExtent](../Topic/COleServerItem::OnGetExtent.md) proporciona el tamaño natural del elemento al contenedor, habilitando el contenedor para ajustar el tamaño del elemento.  
  
 Para obtener más información sobre servidores y temas relacionados, vea el artículo [Servidores: Implementar en un Servidor](../../mfc/servers-implementing-a-server.md) y “crear un contenedor o una aplicación de servidor” en el artículo [contenedores: Características avanzadas](../../mfc/containers-advanced-features.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)