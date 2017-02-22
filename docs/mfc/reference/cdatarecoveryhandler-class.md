---
title: "CDataRecoveryHandler Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataRecoveryHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataRecoveryHandler class"
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CDataRecoveryHandler Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDataRecoveryHandler` autoguarda documentos y los restablece si existe una aplicación inesperado.  
  
## Sintaxis  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## Members  
  
### Constructores  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](../Topic/CDataRecoveryHandler::CDataRecoveryHandler.md)|Crea un objeto `CDataRecoveryHandler`.|  
  
### Métodos  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveAllDocumentInfo.md)|autoguarda cada archivo registrado con la clase de `CDataRecoveryHandler` .|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](../Topic/CDataRecoveryHandler::AutosaveDocumentInfo.md)|autoguarda el documento especificado.|  
|[CDataRecoveryHandler::CreateDocumentInfo](../Topic/CDataRecoveryHandler::CreateDocumentInfo.md)|agrega un documento a la lista de documentos abiertos.|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](../Topic/CDataRecoveryHandler::DeleteAllAutosavedFiles.md)|elimina todos los archivos autoguardados actuales.|  
|[CDataRecoveryHandler::DeleteAutosavedFile](../Topic/CDataRecoveryHandler::DeleteAutosavedFile.md)|elimina el archivo autoguardado especificado.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](../Topic/CDataRecoveryHandler::GenerateAutosaveFileName.md)|Representa el nombre de un archivo de autoguardado asociado al nombre de archivo proporcionado del documento.|  
|[CDataRecoveryHandler::GetAutosaveInterval](../Topic/CDataRecoveryHandler::GetAutosaveInterval.md)|devuelve el intervalo entre el autoguardado intenta.|  
|[CDataRecoveryHandler::GetAutosavePath](../Topic/CDataRecoveryHandler::GetAutosavePath.md)|Devuelve la ruta de acceso de los archivos autoguardados.|  
|[CDataRecoveryHandler::GetDocumentListName](../Topic/CDataRecoveryHandler::GetDocumentListName.md)|Recupera el nombre de un objeto de `CDocument` .|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](../Topic/CDataRecoveryHandler::GetNormalDocumentTitle.md)|Recupera el título normal para el documento especificado.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](../Topic/CDataRecoveryHandler::GetRecoveredDocumentTitle.md)|Crea y devuelve el título para el documento recuperado.|  
|[CDataRecoveryHandler::GetRestartIdentifier](../Topic/CDataRecoveryHandler::GetRestartIdentifier.md)|Recupera el identificador único del reinicio de la aplicación.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle.md)|Indica si `CDataRecoveryHandler` realiza un autoguardado en el bucle de inactividad actual.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](../Topic/CDataRecoveryHandler::GetShutdownByRestartManager.md)|Indica si el administrador de reinicio produjo la aplicación salir.|  
|[CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md)|Inicializa el objeto `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::QueryRestoreAutosavedDocuments.md)|Muestra un cuadro de diálogo al usuario para cada documento que `CDataRecoveryHandler` autoguardó.  El cuadro de diálogo determina si el usuario desea restaurar el documento autoguardado.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](../Topic/CDataRecoveryHandler::ReadOpenDocumentList.md)|Carga el documento abierto enumerado del registro.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](../Topic/CDataRecoveryHandler::RemoveDocumentInfo.md)|Quita el documento proporcionado de la lista de documento abierto.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](../Topic/CDataRecoveryHandler::ReopenPreviousDocuments.md)|Abra previamente los documentos abiertos.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](../Topic/CDataRecoveryHandler::RestoreAutosavedDocuments.md)|Restaura los documentos autoguardados basados en datos proporcionados por el usuario.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](../Topic/CDataRecoveryHandler::SaveOpenDocumentList.md)|Guarda la lista actual de documentos abiertos al Registro de Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](../Topic/CDataRecoveryHandler::SetAutosaveInterval.md)|Establece el tiempo entre los ciclos de autoguardado en milisegundos.|  
|[CDataRecoveryHandler::SetAutosavePath](../Topic/CDataRecoveryHandler::SetAutosavePath.md)|establece el directorio donde se almacenan los archivos autoguardados.|  
|[CDataRecoveryHandler::SetRestartIdentifier](../Topic/CDataRecoveryHandler::SetRestartIdentifier.md)|Establece el identificador único de reinicio para esta instancia de `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md)|Establece si `CDataRecoveryHandler` guarda la información del documento abierto al Registro de Windows durante el ciclo inactivo actual.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](../Topic/CDataRecoveryHandler::SetShutdownByRestartManager.md)|Establece si el administrador de reinicio produjo la salida anterior de la aplicación.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](../Topic/CDataRecoveryHandler::UpdateDocumentInfo.md)|Actualiza la información de un documento porque el usuario lo guardó.|  
  
### miembros de datos  
  
|||  
|-|-|  
|m\_bRestoringPreviousOpenDocs|indica si el controlador de la recuperación de datos vuelve a abrir previamente documentos abiertos.|  
|m\_bSaveDocumentInfoOnIdle|Indica si el controlador de la recuperación de datos autoguarda documentos en el bucle de inactividad siguiente.|  
|m\_bShutdownByRestartManager|Indica si el administrador de reinicio hace que la aplicación salir.|  
|m\_dwRestartManagerSupportFlags|Marca que indica la compatibilidad que proporciona el administrador de reinicio de la aplicación.|  
|m\_lstAutosavesToDelete|Una lista de archivos autoguardados que no eliminados cuando los documentos originales se han cerrado.  Cuando se cierra la aplicación, el administrador de reinicio reintenta eliminar archivos.|  
|m\_mapDocNameToAutosaveName|Un mapa de los nombres del documento a los nombres de archivo autoguardados.|  
|m\_mapDocNameToDocumentPtr|Un mapa de los nombres de documento a punteros de [CDocument](../../mfc/reference/cdocument-class.md) .|  
|m\_mapDocNameToRestoreBool|Un mapa de los nombres del documento a un parámetro boolean que indica si se debe restablecer el documento autoguardado.|  
|m\_mapDocumentPtrToDocName|Un mapa de los punteros de `CDocument` a los nombres del documento.|  
|m\_mapDocumentPtrToDocTitle|Un mapa de los punteros de `CDocument` los títulos del documento.  Estos nombres se utilizan para guardar archivos.|  
|m\_nAutosaveInterval|tiempo en milisegundos entre los autoguardados.|  
|m\_nTimerID|El identificador del temporizador de autoguardado.|  
|m\_strAutosavePath|La ubicación donde se almacenan los documentos autoguardados.|  
|más m\_strRestartIdentifier|La representación de cadena del GUID para el administrador de reinicio.|  
  
## Comentarios  
 El administrador de reinicio utiliza la clase de `CDataRecoveryHandler` para realizar un seguimiento de todos los documentos abiertos y para autoguardarlos según sea necesario.  para habilitar autoguardado, utilice el método de [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](../Topic/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.md) .  Este método hace que `CDataRecoveryHandler` realizar un autoguardado en el bucle de inactividad siguiente.  El administrador de reinicio llama `SetSaveDocumentInfoOnIdle` cuando `CDataRecoveryHandler` debe realizar un autoguardado.  
  
 todos los métodos de la clase de `CDataRecoveryHandler` son virtuales.  Reemplace los métodos de esta clase para crear dispone el controlador personalizado de recuperación de datos.  A menos que cree posee el controlador de la recuperación de datos o reinicie el administrador, no cree instancias de un CDataRecoveryHandler.  [CWinApp Class](../../mfc/reference/cwinapp-class.md) crea un objeto de `CDataRecoveryHandler` mientras se requiere.  
  
 Antes de poder utilizar un objeto de `CDataRecoveryHandler` , debe llamar a [CDataRecoveryHandler::Initialize](../Topic/CDataRecoveryHandler::Initialize.md).  
  
 Dado que la clase de `CDataRecoveryHandler` está conectada estrechamente con el administrador de reinicio, `CDataRecoveryHandler` depende del parámetro global `m_dwRestartManagerSupportFlags`.  Este parámetro determina los permisos que tiene el administrador de reinicio y cómo interactúa con la aplicación.  Para escribir en una aplicación existente, tiene que asignar `m_dwRestartManagerSupportFlags` el valor adecuado en el constructor de la aplicación principal.  Para obtener más información sobre cómo usar el administrador de reinicio, vea [Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md).  
  
## Requisitos  
 **encabezado:** afxdatarecovery.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)