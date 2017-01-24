---
title: "Contenci&#243;n de documentos activos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de documentos activos [C++], acerca de contenedores de documentos activos"
  - "documentos activos [C++], contenedores"
  - "contenedores [C++], documento activo"
  - "MFC [C++], compatibilidad con COM"
  - "MFC COM [C++], contención de documentos activos"
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenci&#243;n de documentos activos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contención de documento activo es una tecnología que proporciona un único cuadro en el que trabajar con documentos, en lugar de forzarle para crear y utilizar los cuadros de aplicación múltiple para cada tipo de documento.  Diferencia de tecnología OLE básica en que OLE funciona con objetos incrustados dentro de un documento compuesto en el que sólo una parte única de contenido puede estar activo.  Con la contención de documento activo, se genera un documento \(es decir, una aplicación completa, incluidos menús, barras de herramientas asociados, etc.\) en el contexto de un fotograma.  
  
 La tecnología de contención de documento activo se desarrolló originalmente para que Microsoft Office implementada en Office binder.  Sin embargo, la tecnología es bastante flexible admitir los contenedores del documento activo distinto de Office binder y puede admitir los servidores de documento distinto de Office y aplicaciones compatibles con Office.  
  
 La aplicación que los documentos activos de los host se denominan [contenedor de documentos activos](../mfc/active-document-containers.md).  Ejemplos de estos contenedores son el cuaderno o Microsoft Internet Explorer de Microsoft Office.  
  
 Se implementa la contención del documento activo como un conjunto de extensiones a documentos de OLE, la tecnología de documento compuesto de OLE.  Las extensiones son las interfaces adicionales que permiten que un objeto integrable, en contexto representa un documento en lugar de una parte única de contenido incrustado.  Como con documentos de OLE, contención de documento activo utiliza un contenedor que proporcione espacio de pantalla para los documentos activos, y los servidores que proporcionan funciones para los documentos activos propios de la interfaz de usuario y manipulación.  
  
 [servidor de documentos activos](../mfc/active-document-servers.md) es una aplicación \(como word, Excel, o PowerPoint\) que admite una o más clases de documento activo, donde cada objeto propio admite las interfaces de extensión que permiten que el objeto está activa en un contenedor adecuado.  
  
 [documento activo](../mfc/active-documents.md) \(proporcionado de un servidor de documentos activos como word o Excel\) es esencialmente un documento completo, convencional que se incrusta como objeto dentro de otro contenedor de documentos activos.  A diferencia de objetos incrustados, los documentos activos tienen control total sobre las páginas, y la interfaz completa de la aplicación \(con todos los comandos y herramientas subyacentes\) está disponible al usuario editarlas.  
  
 Un documento activo es mejor entiende distinguiéndolo de un objeto incrustado OLE estándar.  Después de la convención OLE, un objeto incrustado es el que se muestra dentro de la página del documento que su propietario, y el documento es administrado por un contenedor OLE.  El contenedor almacena los datos de objeto incrustado con el resto del documento.  Sin embargo, los objetos incrustados se limitan en que no controlan la página en la que aparecen.  
  
 Los usuarios de una aplicación contenedora de documentos activos pueden crear documentos activos \(denominados secciones en Office binder\) mediante las aplicaciones favoritas \(proporcionadas estas aplicaciones es el documento activo habilitado\), con todos los usuarios pueden administrar el proyecto resultante como una entidad única, que puede ser denominada, únicamente guardado, formulario, y así sucesivamente.  De la misma manera, un usuario de un explorador de Internet puede tratar la red completa, así como los sistemas de archivos locales, como una entidad única de almacenamiento de documento con la capacidad de examinar documentos en ese almacén de una ubicación.  
  
## Programas de ejemplo  
  
-   El ejemplo de [MFCBIND](../top/visual-cpp-samples.md) muestra la implementación de una aplicación contenedora del documento activo.  
  
## Vea también  
 [MFC COM](../mfc/mfc-com.md)