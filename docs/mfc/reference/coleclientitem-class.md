---
title: "COleClientItem Class | Microsoft Docs"
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
  - "COleClientItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "client items and OLE containers"
  - "COleClientItem class"
  - "container interface class"
  - "OLE client item class"
  - "OLE containers, client items"
  - "OLE containers, clase de interfaz"
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleClientItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define la interfaz del contenedor a elementos de OLE.  
  
## Sintaxis  
  
```  
class COleClientItem : public CDocItem  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleClientItem::COleClientItem](../Topic/COleClientItem::COleClientItem.md)|Crea un objeto `COleClientItem`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleClientItem::Activate](../Topic/COleClientItem::Activate.md)|Abra el elemento OLE para una operación y después ejecutar el verbo especificado.|  
|[COleClientItem::ActivateAs](../Topic/COleClientItem::ActivateAs.md)|Genera el elemento como otro tipo.|  
|[COleClientItem::AttachDataObject](../Topic/COleClientItem::AttachDataObject.md)|Tiene acceso a los datos del objeto OLE.|  
|[COleClientItem::CanCreateFromData](../Topic/COleClientItem::CanCreateFromData.md)|indica si una aplicación contenedora puede crear un objeto incrustado.|  
|[COleClientItem::CanCreateLinkFromData](../Topic/COleClientItem::CanCreateLinkFromData.md)|indica si una aplicación contenedora puede crear un objeto vinculado.|  
|[COleClientItem::CanPaste](../Topic/COleClientItem::CanPaste.md)|Indica si el portapapeles contiene un elemento OLE integrable o estático.|  
|[COleClientItem::CanPasteLink](../Topic/COleClientItem::CanPasteLink.md)|Indica si el portapapeles contiene un elemento OLE enlazable.|  
|[COleClientItem::Close](../Topic/COleClientItem::Close.md)|Cierra un vínculo a un servidor pero no destruye el elemento.|  
|[COleClientItem::ConvertTo](../Topic/COleClientItem::ConvertTo.md)|convierte el elemento a otro tipo.|  
|[COleClientItem::CopyToClipboard](../Topic/COleClientItem::CopyToClipboard.md)|Copia el elemento OLE en el portapapeles.|  
|[COleClientItem::CreateCloneFrom](../Topic/COleClientItem::CreateCloneFrom.md)|crea un duplicado de un elemento existente.|  
|[COleClientItem::CreateFromClipboard](../Topic/COleClientItem::CreateFromClipboard.md)|Crea un elemento incrustado del portapapeles.|  
|[COleClientItem::CreateFromData](../Topic/COleClientItem::CreateFromData.md)|crea un elemento incrustado de un objeto de datos.|  
|[COleClientItem::CreateFromFile](../Topic/COleClientItem::CreateFromFile.md)|crea un elemento incrustado de un archivo.|  
|[COleClientItem::CreateLinkFromClipboard](../Topic/COleClientItem::CreateLinkFromClipboard.md)|Crea un elemento vinculado del portapapeles.|  
|[COleClientItem::CreateLinkFromData](../Topic/COleClientItem::CreateLinkFromData.md)|crea un elemento vinculado de un objeto de datos.|  
|[COleClientItem::CreateLinkFromFile](../Topic/COleClientItem::CreateLinkFromFile.md)|crea un elemento vinculado de un archivo.|  
|[COleClientItem::CreateNewItem](../Topic/COleClientItem::CreateNewItem.md)|Crea un nuevo elemento incrustado iniciar la aplicación de servidor.|  
|[COleClientItem::CreateStaticFromClipboard](../Topic/COleClientItem::CreateStaticFromClipboard.md)|Crea un elemento estático del portapapeles.|  
|[COleClientItem::CreateStaticFromData](../Topic/COleClientItem::CreateStaticFromData.md)|crea un elemento estático de un objeto de datos.|  
|[COleClientItem::Deactivate](../Topic/COleClientItem::Deactivate.md)|desactiva el elemento.|  
|[COleClientItem::DeactivateUI](../Topic/COleClientItem::DeactivateUI.md)|restablece la interfaz de usuario de la aplicación contenedora a su estado original.|  
|[COleClientItem::Delete](../Topic/COleClientItem::Delete.md)|Elimina o cerrar el elemento OLE si fuera un elemento vinculado.|  
|[COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)|Realiza una operación de arrastrar y colocar.|  
|[COleClientItem::DoVerb](../Topic/COleClientItem::DoVerb.md)|ejecuta el verbo especificado.|  
|[COleClientItem::Draw](../Topic/COleClientItem::Draw.md)|Dibuja el elemento.|  
|[COleClientItem::GetActiveView](../Topic/COleClientItem::GetActiveView.md)|Obtiene la vista en la que el elemento se provoca en contexto.|  
|[COleClientItem::GetCachedExtent](../Topic/COleClientItem::GetCachedExtent.md)|Devuelve los límites del rectángulo OLE del elemento.|  
|[COleClientItem::GetClassID](../Topic/COleClientItem::GetClassID.md)|Obtiene el identificador de la clase de elemento actual|  
|[COleClientItem::GetClipboardData](../Topic/COleClientItem::GetClipboardData.md)|Obtiene los datos que se colocarían en el portapapeles llamando a la función miembro de `CopyToClipboard` .|  
|[COleClientItem::GetDocument](../Topic/COleClientItem::GetDocument.md)|Devuelve el objeto de `COleDocument` que contiene el elemento actual.|  
|[COleClientItem::GetDrawAspect](../Topic/COleClientItem::GetDrawAspect.md)|Obtiene la vista actual del elemento para generar.|  
|[COleClientItem::GetExtent](../Topic/COleClientItem::GetExtent.md)|Devuelve los límites del rectángulo OLE del elemento.|  
|[COleClientItem::GetIconFromRegistry](../Topic/COleClientItem::GetIconFromRegistry.md)|Retrives un identificador a un icono asociado con el servidor de CLSID determinado.|  
|[COleClientItem::GetIconicMetafile](../Topic/COleClientItem::GetIconicMetafile.md)|Obtiene el metarchivo utilizado para dibujar el icono del elemento.|  
|[COleClientItem::GetInPlaceWindow](../Topic/COleClientItem::GetInPlaceWindow.md)|Devuelve un puntero a la ventana de edición en el contexto del elemento.|  
|[COleClientItem::GetItemState](../Topic/COleClientItem::GetItemState.md)|Obtiene el estado actual del elemento.|  
|[COleClientItem::GetLastStatus](../Topic/COleClientItem::GetLastStatus.md)|Devuelve el estado de la operación OLE última.|  
|[COleClientItem::GetLinkUpdateOptions](../Topic/COleClientItem::GetLinkUpdateOptions.md)|Devuelve el modo de actualización para un elemento vinculado \(característica avanzada\).|  
|[COleClientItem::GetType](../Topic/COleClientItem::GetType.md)|Devuelve el tipo \(insertado, vinculado, o static\) del elemento.|  
|[COleClientItem::GetUserType](../Topic/COleClientItem::GetUserType.md)|Obtiene una cadena que describe el tipo de elemento.|  
|[COleClientItem::IsInPlaceActive](../Topic/COleClientItem::IsInPlaceActive.md)|Devuelve `TRUE` si el elemento está activo en contexto.|  
|[COleClientItem::IsLinkUpToDate](../Topic/COleClientItem::IsLinkUpToDate.md)|Devuelve **TRUE** si un elemento vinculado está actualizado con el documento de origen.|  
|[COleClientItem::IsModified](../Topic/COleClientItem::IsModified.md)|Devuelve `TRUE` si se ha modificado el elemento desde que se guardó por última vez.|  
|[COleClientItem::IsOpen](../Topic/COleClientItem::IsOpen.md)|Devuelve `TRUE` si el elemento está abierto en la aplicación de servidor.|  
|[COleClientItem::IsRunning](../Topic/COleClientItem::IsRunning.md)|Devuelve `TRUE` si la aplicación de servidor de elemento se está ejecutando.|  
|[COleClientItem::OnActivate](../Topic/COleClientItem::OnActivate.md)|Llamado por el marco para notificar al elemento que se produce.|  
|[COleClientItem::OnActivateUI](../Topic/COleClientItem::OnActivateUI.md)|Llamado por el marco para notificar al elemento que se activan y debe mostrar la interfaz de usuario.|  
|[COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md)|Se llama cuando el servidor cambia el elemento.  Implementación necesaria.|  
|[COleClientItem::OnDeactivate](../Topic/COleClientItem::OnDeactivate.md)|Llamado por el marco cuando se desactiva un elemento.|  
|[COleClientItem::OnDeactivateUI](../Topic/COleClientItem::OnDeactivateUI.md)|Llamado por el marco cuando el servidor ha quitado la interfaz de usuario en contexto.|  
|[COleClientItem::OnGetClipboardData](../Topic/COleClientItem::OnGetClipboardData.md)|Llamado por el marco para obtener los datos que se copiarán en el portapapeles.|  
|[COleClientItem::OnInsertMenus](../Topic/COleClientItem::OnInsertMenus.md)|Llamado por el marco para crear un menú compuesto.|  
|[COleClientItem::OnRemoveMenus](../Topic/COleClientItem::OnRemoveMenus.md)|Llamado por el marco para quitar los menús de contenedor de un menú compuesto.|  
|[COleClientItem::OnSetMenu](../Topic/COleClientItem::OnSetMenu.md)|Llamado por el marco para instalar y quitar un menú compuesto.|  
|[COleClientItem::OnShowControlBars](../Topic/COleClientItem::OnShowControlBars.md)|Llamado por el marco para mostrar y ocultar las barras de controles.|  
|[COleClientItem::OnUpdateFrameTitle](../Topic/COleClientItem::OnUpdateFrameTitle.md)|Llamado por el marco para actualizar la barra de título de la ventana de marco.|  
|[COleClientItem::ReactivateAndUndo](../Topic/COleClientItem::ReactivateAndUndo.md)|Reactivar el elemento y deshace la última operación de la edición en contexto.|  
|[COleClientItem::Release](../Topic/COleClientItem::Release.md)|Libera la conexión OLE vincularon el elemento y cierre él si estaba abierto.  No destruye el elemento customer.|  
|[COleClientItem::Reload](../Topic/COleClientItem::Reload.md)|Recarga el elemento después de una llamada a `ActivateAs`.|  
|[COleClientItem::Run](../Topic/COleClientItem::Run.md)|Ejecute la aplicación asociado al elemento.|  
|[COleClientItem::SetDrawAspect](../Topic/COleClientItem::SetDrawAspect.md)|Establece la vista actual del elemento para generar.|  
|[COleClientItem::SetExtent](../Topic/COleClientItem::SetExtent.md)|Establece el rectángulo delimitador del elemento.|  
|[COleClientItem::SetHostNames](../Topic/COleClientItem::SetHostNames.md)|Establece los nombres que el servidor muestra al editar el elemento.|  
|[COleClientItem::SetIconicMetafile](../Topic/COleClientItem::SetIconicMetafile.md)|Almacena en memoria caché el metarchivo utilizado para dibujar el icono del elemento.|  
|[COleClientItem::SetItemRects](../Topic/COleClientItem::SetItemRects.md)|Establece el rectángulo delimitador del elemento.|  
|[COleClientItem::SetLinkUpdateOptions](../Topic/COleClientItem::SetLinkUpdateOptions.md)|Establece el modo de actualización para un elemento vinculado \(característica avanzada\).|  
|[COleClientItem::SetPrintDevice](../Topic/COleClientItem::SetPrintDevice.md)|Establece el dispositivo de IMPR\-destino para este elemento de cliente.|  
|[COleClientItem::UpdateLink](../Topic/COleClientItem::UpdateLink.md)|Actualiza la memoria caché de un elemento.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleClientItem::CanActivate](../Topic/COleClientItem::CanActivate.md)|Llamado por el marco para determinar si la activación en contexto está permitida.|  
|[COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)|Llamado por el marco cuando cambia de posición de un elemento.|  
|[COleClientItem::OnDeactivateAndUndo](../Topic/COleClientItem::OnDeactivateAndUndo.md)|Llamado por el marco para deshacer después de activación.|  
|[COleClientItem::OnDiscardUndoState](../Topic/COleClientItem::OnDiscardUndoState.md)|Llamado por el marco para descartar la información de estado de deshacer del elemento.|  
|[COleClientItem::OnGetClipRect](../Topic/COleClientItem::OnGetClipRect.md)|Llamado por el marco para obtener el recortes\-rectángulo de elemento coordina.|  
|[COleClientItem::OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md)|Llamado por el marco para obtener la posición del elemento respecto a la vista.|  
|[COleClientItem::OnGetWindowContext](../Topic/COleClientItem::OnGetWindowContext.md)|Llamado por el marco cuando un elemento se provoca en contexto.|  
|[COleClientItem::OnScrollBy](../Topic/COleClientItem::OnScrollBy.md)|Llamado por el marco para desplazar el elemento en la vista.|  
|[COleClientItem::OnShowItem](../Topic/COleClientItem::OnShowItem.md)|Llamado por el marco para mostrar el elemento.|  
  
## Comentarios  
 Un elemento OLE representa los datos, creados y mantenidos por una aplicación de servidor, que puede ser “sin problemas” escribir en un documento de modo que se presenta al usuario sea un documento único.  El resultado es un “documento compuesto” compuesto de elemento OLE y un documento que contiene.  
  
 Un elemento OLE puede incrustar o vincular.  Si se incrusta, sus datos se almacena como parte del documento compuesto.  Si está vinculado, los datos están almacenados como parte de un archivo independiente creado por la aplicación de servidor, y solo un vínculo a ese archivo se almacena en el documento compuesto.  Todos los elementos de OLE contienen información que especifica la aplicación de servidor que se debe llamar a para editarlos.  
  
 `COleClientItem` define varias funciones reemplazables que se llama en respuesta a las solicitudes de la aplicación de servidor; estos overridables actúan normalmente como notificaciones.  Esto permite que la aplicación de servidor para informar al contenedor cambios que el usuario crea al editar el elemento OLE, o para recuperar la información necesaria durante la edición.  
  
 `COleClientItem` se puede utilizar con la clase de [COleDocument](../../mfc/reference/coledocument-class.md), de [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), o de [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) .  Para utilizar `COleClientItem`, derive una clase de ella y implementar la función miembro de [OnChange](../Topic/COleClientItem::OnChange.md) , que define cómo el contenedor responde a los cambios realizados en el elemento.  Para admitir la activación en contexto, reemplace la función miembro de [OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md) .  Esta función proporciona información sobre la posición indicada del elemento.  
  
 Para obtener más información sobre cómo utilizar la interfaz del contenedor, vea los artículos [contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md) y [activación](../../mfc/activation-cpp.md).  
  
> [!NOTE]
>  [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] hace referencia a elementos incrustados y vinculados como “objetos” y hacer referencia a tipos de elementos como “clases”. Esta referencia utiliza el término “elemento” para distinguir la entidad\) del objeto correspondiente de C\+\+ y el término “tipo” para distinguir la categoría OLE de clase de C\+\+.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo MFCBIND de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo OCLIENT de MFC](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)