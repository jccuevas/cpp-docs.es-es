---
title: Compatibilidad con documentos, Asistente para aplicaciones MFC compuestos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.compdoc
dev_langs: C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9390f3849cd7511054f1248205c5d2c408cb7e71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compound-document-support-mfc-application-wizard"></a>Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC
En esta página del Asistente para aplicaciones MFC, indicar a qué nivel de la aplicación proporciona compatibilidad con documentos compuestos y activa. La aplicación debe admitir la arquitectura documento/vista para admitir los documentos compuestos y plantillas de documento.  
  
 De forma predeterminada, la aplicación no contiene ninguna compatibilidad con documentos compuestos. Si acepta esta configuración predeterminada, la aplicación no admite documentos activos o los archivos compuestos.  
  
 **Compatibilidad con documentos compuestos**  
 Determina si la aplicación proporciona compatibilidad con el contenedor, compatibilidad con el servidor o ambos. Para obtener más información acerca de esta área, vea:  
  
-   [Contenedores: Implementar un contenedor](../../mfc/containers-implementing-a-container.md)  
  
-   [Servidores: Implementar un servidor](../../mfc/servers-implementing-a-server.md)  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ninguno**|Indica ninguna compatibilidad para el objeto de vinculación e incrustación de objetos (OLE). De forma predeterminada, el Asistente para aplicaciones crea una aplicación sin compatibilidad con ActiveX.|  
|**Contenedor**|Contiene objetos vinculados e incrustados.|  
|**Miniservidor**|Indica que la aplicación puede crear y administrar objetos de documento compuesto. Tenga en cuenta que no se pueden ejecutar servidores mini actuar por sí sola y sólo admiten objetos incrustados.|  
|**Servidor completo**|Indica que la aplicación puede crear y administrar objetos de documento compuesto. Servidores completos son capaces de ejecutar de forma independiente y admiten tanto objetos vinculados como elementos incrustan.|  
|**Contenedor o servidor completo**|Indica que la aplicación puede ser un contenedor y un servidor. Un contenedor es una aplicación que puede incorporar elementos incrustados o vinculados en sus propios documentos. Un servidor es una aplicación que puede crear elementos de automatización para su uso por aplicaciones de contenedor.|  
  
 **Opciones adicionales**  
 Indica si la aplicación admite documentos activos. Vea [documentos activos](../../mfc/active-documents.md) para obtener más información acerca de esta característica.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Servidor de documentos activos**|Indica que la aplicación puede crear y administrar documentos activos. Si selecciona esta opción, debe especificar una extensión de archivo para el servidor del documento activo en el **la extensión de archivo** cuadro el [cadenas de plantillas de documento](../../mfc/reference/document-template-strings-mfc-application-wizard.md) página del asistente. Vea [servidores de documentos activos](../../mfc/active-document-servers.md) para obtener más información.|  
|**Contenedor de documentos activos**|Indica que la aplicación puede contener documentos activos en su marco. Documentos activos pueden incluir, por ejemplo, documentos de Internet Explorer o documentos de Office, como archivos de Microsoft Word u hojas de cálculo de Excel. Vea [contención de documentos activos](../../mfc/active-document-containment.md) para obtener más información.|  
|**Compatibilidad con archivos compuestos**|No serializa los documentos de la aplicación contenedora con el formato de archivo compuesto. Esta opción fuerza la carga de un archivo completo que contiene objetos en memoria. Guarda incremental a objetos individuales no está disponible. Si un objeto se cambia y se guardan posteriormente, se guardan todos los objetos en el archivo.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)

