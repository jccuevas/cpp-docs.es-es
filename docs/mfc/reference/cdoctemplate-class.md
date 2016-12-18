---
title: "CDocTemplate Class | Microsoft Docs"
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
  - "CDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocTemplate class"
  - "plantillas de documento"
  - "plantillas, documento"
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase abstracta que define la funcionalidad básica para las plantillas de documento.  
  
## Sintaxis  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](../Topic/CDocTemplate::CDocTemplate.md)|Crea un objeto `CDocTemplate`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](../Topic/CDocTemplate::AddDocument.md)|Agrega un documento a una plantilla.|  
|[CDocTemplate::CloseAllDocuments](../Topic/CDocTemplate::CloseAllDocuments.md)|Cierre todos los documentos asociados a esta plantilla.|  
|[CDocTemplate::CreateNewDocument](../Topic/CDocTemplate::CreateNewDocument.md)|crea un nuevo documento.|  
|[CDocTemplate::CreateNewFrame](../Topic/CDocTemplate::CreateNewFrame.md)|Crea una nueva ventana de marco que contiene un documento y una vista.|  
|[CDocTemplate::CreateOleFrame](../Topic/CDocTemplate::CreateOleFrame.md)|Crea una ventana OLE\- habilitada de marco.|  
|[CDocTemplate::CreatePreviewFrame](../Topic/CDocTemplate::CreatePreviewFrame.md)|Crea un marco secundario utilizado para la vista previa enriquecidas.|  
|[CDocTemplate::GetDocString](../Topic/CDocTemplate::GetDocString.md)|Recupera una cadena asociado al tipo de documento.|  
|[CDocTemplate::GetFirstDocPosition](../Topic/CDocTemplate::GetFirstDocPosition.md)|Recupera la posición del primer documento asociado a esta plantilla.|  
|[CDocTemplate::GetNextDoc](../Topic/CDocTemplate::GetNextDoc.md)|Recupera un documento y la posición del siguiente.|  
|[CDocTemplate::InitialUpdateFrame](../Topic/CDocTemplate::InitialUpdateFrame.md)|Inicializa la ventana de marco, y opcionalmente hace visible.|  
|[CDocTemplate::LoadTemplate](../Topic/CDocTemplate::LoadTemplate.md)|Carga los recursos para `CDocTemplate` o una clase derivada especificado.|  
|[CDocTemplate::MatchDocType](../Topic/CDocTemplate::MatchDocType.md)|determina el grado de confianza en la coincidencia entre un tipo de documento y esta plantilla.|  
|[CDocTemplate::OpenDocumentFile](../Topic/CDocTemplate::OpenDocumentFile.md)|Abra un archivo especificado por un nombre de ruta de acceso.|  
|[CDocTemplate::RemoveDocument](../Topic/CDocTemplate::RemoveDocument.md)|Quita un documento de una plantilla.|  
|[CDocTemplate::SaveAllModified](../Topic/CDocTemplate::SaveAllModified.md)|Guarda todos los documentos asociados a esta plantilla se hayan modificado.|  
|[CDocTemplate::SetContainerInfo](../Topic/CDocTemplate::SetContainerInfo.md)|Determina los recursos para los contenedores de OLE al editar un elemento OLE en contexto.|  
|[CDocTemplate::SetDefaultTitle](../Topic/CDocTemplate::SetDefaultTitle.md)|Muestra el título predeterminado en la barra de título de la ventana de documento.|  
|[CDocTemplate::SetPreviewInfo](../Topic/CDocTemplate::SetPreviewInfo.md)|Configuración fuera del controlador de la vista previa.|  
|[CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md)|Determina los recursos y las clases cuando se inserta el documento del servidor o en contexto editado.|  
  
## Comentarios  
 Se suele crear una o más plantillas de documento en la implementación de la función de `InitInstance` de la aplicación.  Una plantilla de documento define las relaciones entre tres tipos de clases:  
  
-   Una clase de documento, que se deriva de **CDocument**.  
  
-   Una clase de vista, que muestra los datos de la clase document enumerados anteriormente.  Puede derivar esta clase de `CView`, de `CScrollView`, de `CFormView`, o de `CEditView`.  \(También puede usar `CEditView` directamente.\)  
  
-   Una clase de ventana de marco, que contiene la vista.  Para una aplicación de \(SDI\) de interfaz de un único documento, derive esta clase de `CFrameWnd`.  Para una aplicación de \(MDI\) de interfaz de múltiples documentos, derive esta clase de `CMDIChildWnd`.  Si no necesita personalizar el comportamiento de la ventana de marco, puede utilizar `CFrameWnd` o `CMDIChildWnd` directamente sin derivar su propia clase.  
  
 La aplicación tiene una plantilla de documento para cada tipo de documento que admite.  Por ejemplo, si la aplicación admite hojas de cálculo y documentos de texto, la aplicación tiene dos objetos de plantilla de documento.  Cada plantilla de documento es responsable de crear y administrar todos los documentos de su tipo.  
  
 Plantilla de documento almacena punteros a objetos de `CRuntimeClass` para el documento, vista, y las clases de ventana de marco.  Se especifican estos objetos de `CRuntimeClass` al crear una plantilla de documento.  
  
 Plantilla de documento contiene el id. de los recursos utilizados con el tipo de documento \(como menú, icono, o recursos de la tabla de aceleradores\).  Plantilla de documento también tiene cadenas que contienen información adicional sobre el tipo de documento.  Éstos incluyen el nombre de tipo de documento \(por ejemplo, “hoja de cálculo”\) y la extensión de archivo \(por ejemplo, “.xls”\).  Opcionalmente, puede contener otras cadenas utilizadas por la interfaz de usuario de la aplicación, el administrador de archivos de Windows, y el objeto vinculando e insertar compatibilidad \(OLE\).  
  
 Si la aplicación es un contenedor o servidor OLE, plantilla de documento también define el id. de menú utilizado durante la activación en contexto.  Si la aplicación es un servidor OLE, plantilla de documento define el id. de la barra de herramientas y del menú utilizados durante la activación en contexto.  Especifique estos recursos de OLE adicionales llamando `SetContainerInfo` y `SetServerInfo`.  
  
 Dado que `CDocTemplate` es una clase abstracta, no puede usar la clase directamente.  Una aplicación típica utiliza uno de dos `CDocTemplate`\- clases derivadas proporcionadas por la biblioteca Microsoft Foundation Class: `CSingleDocTemplate`, que implementa el SDI, y `CMultiDocTemplate`, que implementa MDI.  Vea esas clases para obtener más información sobre cómo utilizar las plantillas de documento.  
  
 Si la aplicación requiere un paradigma de la interfaz de usuario que es fundamentalmente diferente SDI o MDI, puede derivar su propia clase de `CDocTemplate`.  
  
 Para obtener más información sobre `CDocTemplate`, vea [Plantillas de documento y el proceso de Creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CEditView Class](../../mfc/reference/ceditview-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)