---
title: "CDocument Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocument class"
  - "control de comandos, documents and"
  - "enrutamiento de comandos, documents and"
  - "documentos [C++], enrutamiento de comandos"
  - "documentos [C++], document classes"
  - "documentos [C++], varias vistas"
  - "documentos [C++], serialización"
  - "archivos [C++], documentos"
  - "serialización [C++], documents and"
  - "vistas [C++], documento"
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad básica para las clases definidas por el usuario del documento.  
  
## Sintaxis  
  
```  
class CDocument : public CCmdTarget  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::CDocument](../Topic/CDocument::CDocument.md)|Crea un objeto `CDocument`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::AddView](../Topic/CDocument::AddView.md)|Adjunta una vista al documento.|  
|[CDocument::BeginReadChunks](../Topic/CDocument::BeginReadChunks.md)|Inicializa la lectura del fragmento.|  
|[CDocument::CanCloseFrame](../Topic/CDocument::CanCloseFrame.md)|Overridable avanzada; se llama antes de cerrar una ventana de marco que ve este documento.|  
|[CDocument::ClearChunkList](../Topic/CDocument::ClearChunkList.md)|Borra la lista de fragmentos.|  
|[CDocument::ClearPathName](../Topic/CDocument::ClearPathName.md)|Borra la ruta de acceso del objeto de documento.|  
|[CDocument::DeleteContents](../Topic/CDocument::DeleteContents.md)|Denominado para realizar la limpieza del documento.|  
|[CDocument::FindChunk](../Topic/CDocument::FindChunk.md)|Busca un fragmento con el GUID especificado.|  
|[CDocument::GetAdapter](../Topic/CDocument::GetAdapter.md)|Devuelve un puntero al objeto que implementa la interfaz de `IDocument` .|  
|[CDocument::GetDocTemplate](../Topic/CDocument::GetDocTemplate.md)|Devuelve un puntero a la plantilla de documento que describe el tipo de documento.|  
|[CDocument::GetFile](../Topic/CDocument::GetFile.md)|Devuelve un puntero al objeto deseado de `CFile` .|  
|[CDocument::GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md)|Devuelve la posición del primero en la lista de vistas; se utiliza para iniciar iteración.|  
|[CDocument::GetNextView](../Topic/CDocument::GetNextView.md)|Recorre en iteración la lista de vistas asociado al documento.|  
|[CDocument::GetPathName](../Topic/CDocument::GetPathName.md)|Devuelve la ruta de acceso del archivo del documento.|  
|[CDocument::GetThumbnail](../Topic/CDocument::GetThumbnail.md)|Denominado para crear un mapa de bits que va a utilizar el proveedor de miniaturas para mostrar la miniatura.|  
|[CDocument::GetTitle](../Topic/CDocument::GetTitle.md)|Devuelve el título del documento.|  
|[CDocument::InitializeSearchContent](../Topic/CDocument::InitializeSearchContent.md)|Denominado para inicializar contenido de búsqueda para el controlador de búsqueda.|  
|[CDocument::IsModified](../Topic/CDocument::IsModified.md)|Indica si se ha modificado el documento desde que se guardó por última vez.|  
|[CDocument::IsSearchAndOrganizeHandler](../Topic/CDocument::IsSearchAndOrganizeHandler.md)|Indica si esta instancia`CDocument` del objeto se creó para la búsqueda y organizar el controlador.|  
|[CDocument::LoadDocumentFromStream](../Topic/CDocument::LoadDocumentFromStream.md)|Denominado para cargar datos de la secuencia.|  
|[CDocument::OnBeforeRichPreviewFontChanged](../Topic/CDocument::OnBeforeRichPreviewFontChanged.md)|Se llama antes de cambiar la fuente de vista previa enriquecidas.|  
|[CDocument::OnChangedViewList](../Topic/CDocument::OnChangedViewList.md)|Se llama después de que una vista se agregue a o se quite del documento.|  
|[CDocument::OnCloseDocument](../Topic/CDocument::OnCloseDocument.md)|denominado para cerrar el documento.|  
|[CDocument::OnCreatePreviewFrame](../Topic/CDocument::OnCreatePreviewFrame.md)|Llamado por el marco cuando necesita crear un cuadro de vista previa para la vista previa enriquecidas.|  
|[CDocument::OnDocumentEvent](../Topic/CDocument::OnDocumentEvent.md)|Llamado por el marco en respuesta a un evento de documento.|  
|[CDocument::OnDrawThumbnail](../Topic/CDocument::OnDrawThumbnail.md)|Invalide este método en una clase derivada para dibujar el contenido de miniaturas.|  
|[CDocument::OnLoadDocumentFromStream](../Topic/CDocument::OnLoadDocumentFromStream.md)|Llamado por el marco cuando necesita cargar los datos de la secuencia.|  
|[CDocument::OnNewDocument](../Topic/CDocument::OnNewDocument.md)|denominado para crear un nuevo documento.|  
|[CDocument::OnOpenDocument](../Topic/CDocument::OnOpenDocument.md)|denominado para abrir un documento existente.|  
|[CDocument::OnPreviewHandlerQueryFocus](../Topic/CDocument::OnPreviewHandlerQueryFocus.md)|Indica al controlador preview devolver el HWND de llamar a la función de GetFocus.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](../Topic/CDocument::OnPreviewHandlerTranslateAccelerator.md)|Indica al controlador preview controlar una pulsación de tecla última hacia arriba de suministro de mensajes del proceso en el que el controlador preview ejecuta.|  
|[CDocument::OnRichPreviewBackColorChanged](../Topic/CDocument::OnRichPreviewBackColorChanged.md)|Se llama cuando el color de fondo de la vista previa enriquecidas ha cambiado.|  
|[CDocument::OnRichPreviewFontChanged](../Topic/CDocument::OnRichPreviewFontChanged.md)|Llamado cuando la fuente de vista previa enriquecidas ha cambiado.|  
|[CDocument::OnRichPreviewSiteChanged](../Topic/CDocument::OnRichPreviewSiteChanged.md)|Se llama cuando el sitio de la vista previa enriquecidas ha cambiado.|  
|[CDocument::OnRichPreviewTextColorChanged](../Topic/CDocument::OnRichPreviewTextColorChanged.md)|Se llama cuando el color del texto de la vista previa enriquecidas ha cambiado.|  
|[CDocument::OnSaveDocument](../Topic/CDocument::OnSaveDocument.md)|Denominado para guardar el documento en el disco.|  
|[CDocument::OnUnloadHandler](../Topic/CDocument::OnUnloadHandler.md)|Llamado por el marco cuando se descarga el controlador preview.|  
|[CDocument::PreCloseFrame](../Topic/CDocument::PreCloseFrame.md)|Se llama antes de la ventana de marco se cierra.|  
|[CDocument::ReadNextChunkValue](../Topic/CDocument::ReadNextChunkValue.md)|Valor del siguiente fragmento de las lecturas.|  
|[CDocument::ReleaseFile](../Topic/CDocument::ReleaseFile.md)|Libere un archivo para que quede disponible para su uso en otras aplicaciones.|  
|[CDocument::RemoveChunk](../Topic/CDocument::RemoveChunk.md)|Quita un fragmento con el GUID especificado.|  
|[CDocument::RemoveView](../Topic/CDocument::RemoveView.md)|Desasocia una vista en el documento.|  
|[CDocument::ReportSaveLoadException](../Topic/CDocument::ReportSaveLoadException.md)|Overridable avanzada; llamado cuando una operación abierto o de guardar no se puede completar debido a una excepción.|  
|[CDocument::SaveModified](../Topic/CDocument::SaveModified.md)|Overridable avanzada; denominado para preguntar al usuario si el documento debe protegerse.|  
|[CDocument::SetChunkValue](../Topic/CDocument::SetChunkValue.md)|Establece un valor de fragmento.|  
|[CDocument::SetModifiedFlag](../Topic/CDocument::SetModifiedFlag.md)|Establece una marca que indica que se ha modificado el documento desde que fue guardado por última vez.|  
|[CDocument::SetPathName](../Topic/CDocument::SetPathName.md)|Establece la ruta de acceso del archivo de datos utilizado por el documento.|  
|[CDocument::SetTitle](../Topic/CDocument::SetTitle.md)|Establece el título del documento.|  
|[CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)|Notifica a todas las vistas que se ha modificado el documento.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)|Envía un mensaje de correo con el documento asociado.|  
|[CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)|Habilita el comando de correo Send si la compatibilidad de correo está presente.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocument::m\_bGetThumbnailMode](../Topic/CDocument::m_bGetThumbnailMode.md)|Especifica que el objeto de `CDocument` creó el dllhost para las miniaturas.  Debe protegerse `CView::OnDraw`.|  
|[CDocument::m\_bPreviewHandlerMode](../Topic/CDocument::m_bPreviewHandlerMode.md)|Especifica que el objeto de `CDocument` creó el prevhost para `Rich Preview`.  Debe protegerse `CView::OnDraw`.|  
|[CDocument::m\_bSearchMode](../Topic/CDocument::m_bSearchMode.md)|Especifica que el objeto de `CDocument` creó el indizador u otra aplicación de búsqueda.|  
|[CDocument::m\_clrRichPreviewBackColor](../Topic/CDocument::m_clrRichPreviewBackColor.md)|Especifica el color de fondo de la ventana de vista previa enriquecidas.  este color es establecido por el host.|  
|[CDocument::m\_clrRichPreviewTextColor](../Topic/CDocument::m_clrRichPreviewTextColor.md)|Especifica el color de primer plano de la ventana de vista previa enriquecidas.  este color es establecido por el host.|  
|[CDocument::m\_lfRichPreviewFont](../Topic/CDocument::m_lfRichPreviewFont.md)|Especifica la fuente de texto de la ventana de vista previa enriquecidas.  Esta información de fuentes establecida por el host.|  
  
## Comentarios  
 Un documento representa la unidad de datos que el usuario abre normalmente con el comando para Abrir archivos y guarda con el comando para guardar archivos.  
  
 **CDocument** admite operaciones estándar como crear un documento, cargarlo, y guardarlo.  El marco manipular documentos mediante la interfaz definida por **CDocument**.  
  
 Una aplicación puede admitir más de un tipo de documento; por ejemplo, una aplicación podría admitir las hojas de cálculo y documentos de texto.  Cada tipo de documento tiene una plantilla de documento asociado; plantilla de documento especifica qué recursos \(por ejemplo, menú, icono, o tabla de aceleradores\) se utilizan para ese tipo de documento.  Cada documento contiene un puntero al objeto asociado de `CDocTemplate` .  
  
 Los usuarios interactúan con un documento a través de los objetos de [CView](../../mfc/reference/cview-class.md) asociado.  Una vista representa una imagen del documento en una ventana de marco e interpreta los datos proporcionados por el usuario como operaciones en el documento.  Un documento puede tener varias vistas asociado.  Cuando el usuario abre una ventana en un documento, el marco de trabajo crea una vista y la agrega al documento.  Plantilla de documento especifica lo que utilizan el tipo de ventana de la vista y el cuadro para mostrar cada tipo de documento.  
  
 Los documentos son parte de enrutamiento estándar del marco y por consiguiente reciben comandos de los componentes de la interfaz de usuario estándar \(como el elemento de menú para guardar archivos\).  un documento recibe los comandos reenviados por la vista activa.  Si el documento no controla un comando determinado, transmite el comando plantilla de documento que lo administra.  
  
 Cuando se modifican los datos de un documento, cada una de sus vistas debe reflejar esos cambios.  **CDocument** proporciona la función miembro de [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) para que se notifique a las vistas de estos cambios, por lo que las vistas pueden representar según sea necesario.  El marco de trabajo también pide al usuario guardar un archivo modificado antes de cerrarlo.  
  
 Para implementar documentos en una aplicación típica, debe hacer lo siguiente:  
  
-   Derive una clase de **CDocument** para cada tipo de documento.  
  
-   Agregue las variables miembro para almacenar los datos de cada documento.  
  
-   El miembro de implemente funciones para leer y modificar los datos del documento.  Las vistas de documento son los usuarios más importantes de estas funciones miembro.  
  
-   Reemplace la función miembro de [CObject:: serialice](../Topic/CObject::Serialize.md) en la clase document para escribir y leer los datos del documento a y desde el disco.  
  
 **CDocument** admite el envío del documento mediante correo si la compatibilidad de correo \(MAPI\) está presente.  consulte los artículos [MAPI](../../mfc/mapi.md) y [Compatibilidad con MAPI en MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Para obtener más información sobre **CDocument**, vea [serialización](../../mfc/serialization-in-mfc.md), [Temas de la arquitectura documento\/vista](../../mfc/document-view-architecture.md), y [Creación de documentos y vistas](../../mfc/document-view-creation.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDIDOCVW de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [NPP de ejemplo de MFC](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)