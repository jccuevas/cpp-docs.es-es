---
title: "Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.compdoc"
dev_langs: 
  - "C++"
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En esta página del Asistente para aplicaciones MFC debe indicar a qué nivel proporcionará la aplicación compatibilidad con documentos compuestos y documentos activos.  La aplicación debe ofrecer compatibilidad con la arquitectura documento\/vista para ser compatible con documentos compuestos y plantillas de documentos.  
  
 De forma predeterminada, la aplicación no es compatible con los documentos compuestos.  Si acepta esta configuración predeterminada, la aplicación no será compatible con los documentos activos o los archivos compuestos.  
  
 **Compatibilidad con documentos compuestos**  
 Determina si la aplicación proporciona compatibilidad con contenedores, con servidores o con contenedores y servidores.  Para obtener más información acerca de esto, vea:  
  
-   [Contenedores: implementar un contenedor](../../mfc/containers-implementing-a-container.md)  
  
-   [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md)  
  
|Opción|Descripción|  
|------------|-----------------|  
|**None**|Indica que no hay compatibilidad para la Vinculación e incrustación de objetos \(OLE\).  De manera predeterminada, el asistente para aplicaciones crea una aplicación sin compatibilidad con ActiveX.|  
|**Contenedor**|Contiene objetos vinculados e incrustados.|  
|**Miniservidor**|Indica que la aplicación puede crear y administrar objetos de documentos compuestos.  Tenga en cuenta que los miniservidores no pueden ejecutarse de forma independiente y sólo admiten objetos incrustados.|  
|**Servidor completo**|Indica que la aplicación puede crear y administrar objetos de documentos compuestos.  Los servidores completos pueden ejecutarse de forma independiente y admiten tanto objetos vinculados como objetos incrustados.|  
|**Contenedor o servidor completo**|Indica que la aplicación puede ser un contenedor y un servidor a la vez.  Un contenedor es una aplicación que puede incorporar elementos incrustados o vinculados en sus propios documentos.  Un servidor es una aplicación que puede crear elementos de automatización para que los utilicen las aplicaciones contenedoras.|  
  
 **Opciones adicionales**  
 Indica si la aplicación es compatible con los documentos activos.  Vea [Documentos activos](../../mfc/active-documents.md) para obtener más información acerca de esta característica.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Servidor de documentos activos**|Indica que la aplicación puede crear y administrar documentos activos.  Si elige esta opción, debe especificar una extensión de archivo para el servidor de documentos activos en el cuadro **Extensión de archivo** en la página [Cadenas de plantillas de documentos](../../mfc/reference/document-template-strings-mfc-application-wizard.md) del asistente.  Vea [Servidores de documentos activos](../../mfc/active-document-servers.md) para obtener más información.|  
|**Contenedor de documentos activos**|Indica que la aplicación puede contener documentos activos en su marco.  Los documentos activos pueden incluir, por ejemplo, documentos de Internet Explorer o documentos de Office como archivos de Microsoft Word u hojas de cálculo de Excel.  Vea [Contención de documentos activos](../../mfc/active-document-containment.md) para obtener más información.|  
|**Compatibilidad con archivos compuestos**|No serializa los documentos de la aplicación contenedora con el formato de archivo compuesto.  Esta opción fuerza la carga en memoria de un archivo completo que contiene objetos.  No se permite guardar en objetos individuales de forma incremental.  Si se modifica un objeto y después se guarda, se guardarán todos los objetos del archivo.|  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)