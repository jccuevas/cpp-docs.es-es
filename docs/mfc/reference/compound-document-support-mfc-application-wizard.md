---
title: Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
ms.openlocfilehash: 572bb10d8aa2af38858bac50f795fb660d5476b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543044"
---
# <a name="compound-document-support-mfc-application-wizard"></a>Compatibilidad con documentos compuestos, Asistente para aplicaciones MFC

En esta página del Asistente para aplicaciones MFC, indicar a qué nivel de la aplicación proporciona compatibilidad con documentos compuestos y activo. La aplicación debe admitir la arquitectura documento/vista para admitir documentos compuestos y plantillas de documento.

De forma predeterminada, la aplicación no contiene ninguna compatibilidad con documentos compuestos. Si acepta esta configuración predeterminada, la aplicación no admite documentos activos o archivos compuestos.

- **Compatibilidad con documentos compuestos**

   Determina si la aplicación proporciona compatibilidad con contenedores, compatibilidad con el servidor o ambos. Para obtener más información acerca de esta área, vea:

   - [Contenedores: Implementar un contenedor](../../mfc/containers-implementing-a-container.md)

   - [Servidores: Implementar un servidor](../../mfc/servers-implementing-a-server.md)

   |Opción|Descripción|
   |------------|-----------------|
   |**Ninguno**|Indica ninguna compatibilidad para la vinculación e incrustación de objetos (OLE). De forma predeterminada, el Asistente para aplicaciones crea una aplicación sin soporte técnico de ActiveX.|
   |**Contenedor**|Contiene objetos vinculados e incrustados.|
   |**Miniservidor**|Indica que la aplicación puede crear y administrar objetos de documento compuesto. Tenga en cuenta que no se pueden ejecutar miniservidores actuar por sí sola y solo se admiten objetos incrustados.|
   |**Servidor completo**|Indica que la aplicación puede crear y administrar objetos de documento compuesto. Están posible ejecutar de forma independiente y admiten ambos vinculados e incrustados elementos servidores completos.|
   |**Contenedor o servidor completo**|Indica que la aplicación puede ser un contenedor y un servidor. Un contenedor es una aplicación que puede incorporar elementos incrustados o vinculados a sus propios documentos. Un servidor es una aplicación que puede crear elementos de automatización para su uso por aplicaciones de contenedor.|

- **Opciones adicionales**

   Indica si la aplicación admite documentos activos. Consulte [documentos activos](../../mfc/active-documents.md) para obtener más información sobre esta característica.

   |Opción|Descripción|
   |------------|-----------------|
   |**Servidor de documentos activos**|Indica que la aplicación puede crear y administrar documentos activos. Si selecciona esta opción, debe especificar una extensión de archivo para el servidor del documento activo en el **la extensión de archivo** cuadro el [cadenas de plantillas de documento](../../mfc/reference/document-template-strings-mfc-application-wizard.md) página del asistente. Consulte [servidores de documentos activos](../../mfc/active-document-servers.md) para obtener más información.|
   |**Contenedor de documentos activos**|Indica que la aplicación puede contener documentos activos dentro del marco. Documentos activos pueden incluir, por ejemplo, documentos de Internet Explorer o documentos de Office, como archivos de Microsoft Word u hojas de cálculo de Excel. Consulte [contención de documentos activos](../../mfc/active-document-containment.md) para obtener más información.|
   |**Compatibilidad con archivos compuestos**|No se serializa documentos de la aplicación contenedora con el formato de archivo compuesto. Esta opción fuerza la carga de un archivo completo que contiene los objetos en memoria. Guarda incremental para objetos individuales no está disponible. Si un objeto se ha cambiado y se guardan posteriormente, se guardan todos los objetos en el archivo.|

## <a name="see-also"></a>Vea también

[Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)

