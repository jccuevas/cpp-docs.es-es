---
title: "COleServerDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleServerDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerDoc class"
  - "container/server applications"
  - "OLE containers, server documents"
  - "aplicaciones de servidor OLE, managing server documents"
  - "OLE server documents"
  - "server documents, OLE"
  - "servidores, OLE"
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleServerDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para los documentos de servidor OLE.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerDoc::COleServerDoc](../Topic/COleServerDoc::COleServerDoc.md)|Crea un objeto `COleServerDoc`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerDoc::ActivateDocObject](../Topic/COleServerDoc::ActivateDocObject.md)|Genera el documento asociado de DocObject.|  
|[COleServerDoc::ActivateInPlace](../Topic/COleServerDoc::ActivateInPlace.md)|Genera el documento para la edición en contexto.|  
|[COleServerDoc::DeactivateAndUndo](../Topic/COleServerDoc::DeactivateAndUndo.md)|Desactiva la interfaz de usuario del servidor.|  
|[COleServerDoc::DiscardUndoState](../Topic/COleServerDoc::DiscardUndoState.md)|Información de la fase de reversión\-provincia de los descarta.|  
|[COleServerDoc::GetClientSite](../Topic/COleServerDoc::GetClientSite.md)|recupera un puntero a la interfaz subyacente de `IOleClientSite` .|  
|[COleServerDoc::GetEmbeddedItem](../Topic/COleServerDoc::GetEmbeddedItem.md)|Devuelve un puntero a un elemento que representa el documento.|  
|[COleServerDoc::GetItemClipRect](../Topic/COleServerDoc::GetItemClipRect.md)|Devuelve el rectángulo actual de recorte para la edición en contexto.|  
|[COleServerDoc::GetItemPosition](../Topic/COleServerDoc::GetItemPosition.md)|Devuelve el rectángulo de la posición actual, en relación con el área de cliente de la aplicación contenedora, para la edición en contexto.|  
|[COleServerDoc::GetZoomFactor](../Topic/COleServerDoc::GetZoomFactor.md)|Devuelve el factor de zoom en píxeles.|  
|[COleServerDoc::IsDocObject](../Topic/COleServerDoc::IsDocObject.md)|determina si el documento es un DocObject.|  
|[COleServerDoc::IsEmbedded](../Topic/COleServerDoc::IsEmbedded.md)|Indica si el documento se inserta en un documento o contenedor una ejecución independiente.|  
|[COleServerDoc::IsInPlaceActive](../Topic/COleServerDoc::IsInPlaceActive.md)|Devuelve `TRUE` si el elemento se activa actualmente en contexto.|  
|[COleServerDoc::NotifyChanged](../Topic/COleServerDoc::NotifyChanged.md)|Notifica a los contenedores que el usuario ha cambiado el documento.|  
|[COleServerDoc::NotifyClosed](../Topic/COleServerDoc::NotifyClosed.md)|Notifica a los contenedores que ha cerrado el usuario el documento.|  
|[COleServerDoc::NotifyRename](../Topic/COleServerDoc::NotifyRename.md)|Notifica a los contenedores que el usuario ha cambiado el documento.|  
|[COleServerDoc::NotifySaved](../Topic/COleServerDoc::NotifySaved.md)|Notifica a los contenedores que el usuario ha guardado el documento.|  
|[COleServerDoc::OnDeactivate](../Topic/COleServerDoc::OnDeactivate.md)|Llamado por el marco cuando el usuario desactiva un elemento generado en su lugar.|  
|[COleServerDoc::OnDeactivateUI](../Topic/COleServerDoc::OnDeactivateUI.md)|Llamado por el marco para destruir los controles y otros elementos de interfaz de usuario creados para la activación en contexto.|  
|[COleServerDoc::OnDocWindowActivate](../Topic/COleServerDoc::OnDocWindowActivate.md)|Llamado por el marco cuando se activa o desactiva la ventana de marco de documento de contenedor.|  
|[COleServerDoc::OnResizeBorder](../Topic/COleServerDoc::OnResizeBorder.md)|Llamado por el marco cuando se cambia el tamaño de la ventana o la ventana de documento del cuadro de la aplicación contenedora.|  
|[COleServerDoc::OnShowControlBars](../Topic/COleServerDoc::OnShowControlBars.md)|Llamado por el marco para mostrar u ocultar las barras de control para la edición en contexto.|  
|[COleServerDoc::OnUpdateDocument](../Topic/COleServerDoc::OnUpdateDocument.md)|Llamado por el marco cuando se guarda un documento de servidor que es un elemento incrustado, actualizando la copia del contenedor del elemento.|  
|[COleServerDoc::RequestPositionChange](../Topic/COleServerDoc::RequestPositionChange.md)|Cambia la posición del marco de la edición en contexto.|  
|[COleServerDoc::SaveEmbedding](../Topic/COleServerDoc::SaveEmbedding.md)|Indica la aplicación contenedora para guardar el documento.|  
|[COleServerDoc::ScrollContainerBy](../Topic/COleServerDoc::ScrollContainerBy.md)|desplaza el documento contenedor.|  
|[COleServerDoc::UpdateAllItems](../Topic/COleServerDoc::UpdateAllItems.md)|Notifica a los contenedores que el usuario ha cambiado el documento.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](../Topic/COleServerDoc::CreateInPlaceFrame.md)|Llamado por el marco para crear una ventana de marco para la edición en contexto.|  
|[COleServerDoc::DestroyInPlaceFrame](../Topic/COleServerDoc::DestroyInPlaceFrame.md)|Llamado por el marco para destruir una ventana de marco para la edición en contexto.|  
|[COleServerDoc::GetDocObjectServer](../Topic/COleServerDoc::GetDocObjectServer.md)|invalide esta función para crear un nuevo objeto de `CDocObjectServer` y para indicar que este documento es un contenedor de DocObject.|  
|[COleServerDoc::OnClose](../Topic/COleServerDoc::OnClose.md)|Llamado por el marco cuando solicite un contenedor para cerrar el documento.|  
|[COleServerDoc::OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md)|Ejecuta un comando o una ayuda especificado de muestra para el comando.|  
|[COleServerDoc::OnFrameWindowActivate](../Topic/COleServerDoc::OnFrameWindowActivate.md)|Llamado por el marco cuando se activa o desactiva la ventana de marco de contenedor.|  
|[COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md)|Denominado para obtener `COleServerItem` que representa el documento; se utiliza para obtener un elemento incrustado.  Implementación necesaria.|  
|[COleServerDoc::OnReactivateAndUndo](../Topic/COleServerDoc::OnReactivateAndUndo.md)|Llamado por el marco a deshacer los cambios realizados realizados durante la edición en contexto.|  
|[COleServerDoc::OnSetHostNames](../Topic/COleServerDoc::OnSetHostNames.md)|Llamado por el marco cuando un contenedor establece el título de la ventana para un objeto incrustado.|  
|[COleServerDoc::OnSetItemRects](../Topic/COleServerDoc::OnSetItemRects.md)|Llamado por el marco para colocar la ventana cuadro de edición en contexto en la ventana de la aplicación contenedora.|  
|[COleServerDoc::OnShowDocument](../Topic/COleServerDoc::OnShowDocument.md)|Llamado por el marco para mostrar u ocultar el documento.|  
  
## Comentarios  
 Un documento de servidor puede contener objetos de [COleServerItem](../../mfc/reference/coleserveritem-class.md) , que representan al servidor que la interfaz incrustado o vinculado elementos.  Cuando una aplicación de servidor es iniciada por un contenedor para editar un elemento incrustado, el elemento se carga como su propio documento de servidor; el objeto de `COleServerDoc` contiene solo un objeto de `COleServerItem` , que consta de todo el documento.  Cuando una aplicación de servidor es iniciada por un contenedor para editar un elemento vinculado, un documento existente se carga desde el disco; una parte del contenido del documento está resaltado indicar el elemento vinculado.  
  
 los objetos de`COleServerDoc` también pueden contener elementos de la clase de [COleClientItem](../../mfc/reference/coleclientitem-class.md) .  Esto permite crear aplicaciones de contenedor\-Servidor.  El marco de trabajo proporciona funciones para almacenar correctamente los elementos de `COleClientItem` manteniendo los objetos de `COleServerItem` .  
  
 Si lo hace la aplicación de servidor no admitir vínculos, un documento de servidor contendrá siempre sólo un elemento del servidor, que representa el objeto incrustado completo como documento.  Si la aplicación de servidor hace vínculos admiten, debe crear un elemento de servidor cada vez que una selección se copia en el portapapeles.  
  
 Para utilizar `COleServerDoc`, derive una clase de ella y implementar la función miembro de [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) , que permite al servidor admite elementos incrustados.  Derive una clase de `COleServerItem` para implementar elementos en los documentos, y devuelve objetos de esa clase de `OnGetEmbeddedItem`.  
  
 Para admitir vinculados los elementos, `COleServerDoc` proporciona la función miembro de [OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md) .  Puede utilizar la implementación predeterminada o reemplazarlo si tiene poseer la manera de administrar los elementos del documento.  
  
 Necesita un `COleServerDoc`\- clase derivada para cada tipo de documento del servidor que admite la aplicación.  Por ejemplo, si la aplicación de servidor admite hojas de cálculo y gráficos, necesita dos `COleServerDoc`\- clases derivadas.  
  
 Para obtener más información sobre los servidores, vea el artículo [Servidores: Implementar en un Servidor](../../mfc/servers-implementing-a-server.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)