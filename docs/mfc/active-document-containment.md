---
title: Contención de documentos activos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74ad16aa453c6fa0df2c84bd0a0a789b05f83169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="active-document-containment"></a>Contención de documentos activos
Contención de documentos activos es una tecnología que proporciona un marco único en el que se va a trabajar con documentos, en lugar de obligarle a crear y usar varios marcos de aplicación para cada tipo de documento. Difiere de la tecnología OLE básica en que OLE funciona con objetos incrustados en un documento compuesto en el que solo un único fragmento de contenido puede estar activo. Mediante la contención de documentos activos, puede activar un documento completo (es decir, una aplicación completa, incluidos menús asociados, las barras de herramientas etc.) en el contexto de un solo fotograma.  
  
 La tecnología de contención de documentos activos se desarrolló originalmente para que Microsoft Office implementar cuaderno de Office. Sin embargo, la tecnología es lo suficientemente flexible como para admitir los contenedores de documentos activos que no sea de cuaderno de Office y puede admitir servidores de documentos que no sea de aplicaciones compatibles con Office y Office.  
  
 La aplicación que hospeda documentos activos se denomina un [contenedor de documentos activos](../mfc/active-document-containers.md). Ejemplos de estos contenedores son el cuaderno de Microsoft Office o Microsoft Internet Explorer.  
  
 Contención de documentos activos se implementa como un conjunto de extensiones OLE documentos, la tecnología de documentos compuestos de OLE. Las extensiones son interfaces adicionales que permiten que un objeto incrustable, en lugar de representar un documento completo en lugar de un único fragmento de contenido incrustado. Al igual que con los documentos OLE, contención de documentos activos utiliza un contenedor que proporciona el espacio de visualización de documentos activos y servidores que proporcionan funciones de interfaz y la manipulación de usuario para los documentos activos.  
  
 Un [servidor de documentos activos](../mfc/active-document-servers.md) es una aplicación (como Word, Excel o PowerPoint) que admite una o más clases de documento activo, donde cada objeto en sí es compatible con las interfaces de extensión que permiten el objeto que se debe activar en un contenedor adecuado.  
  
 Un [documento activo](../mfc/active-documents.md) (proporcionado por un servidor de documentos activos como Word o Excel) es esencialmente un documento convencional que se incrusta como un objeto dentro de otro contenedor de documentos activos. A diferencia de los objetos incrustados, documentos activos tienen control completo sobre sus páginas y toda la interfaz de la aplicación (con todos sus subyacente comandos y herramientas) está disponible para el usuario para modificarlos.  
  
 Un documento activo se entiende mejor comparándolo con un objeto OLE incrustado estándar. Según la norma OLE, un objeto incrustado es aquel que se muestra en la página del documento que es su propietario y el documento está administrado por un contenedor OLE. El contenedor almacena los datos del objeto incrustado con el resto del documento. Sin embargo, los objetos incrustados están limitados a no controlan la página en el que aparecen.  
  
 Los usuarios de una aplicación de contenedor de documentos activos pueden crear documentos activos (denominados secciones en cuaderno de Office) con sus aplicaciones favoritas (siempre que estas aplicaciones admiten documentos activos), pero los usuarios pueden administrar el proyecto resultante como un entidad única, que puede tener forma única el nombre, guardar, imprimir, y así sucesivamente. En la misma manera, un usuario de un explorador de Internet puede tratar la toda la red, así como los sistemas de archivos locales, como una entidad de almacenamiento de único documento con la capacidad de examinar los documentos en que el almacenamiento desde una sola ubicación.  
  
## <a name="sample-programs"></a>Programas de ejemplo  
  
-   El [MFCBIND](../visual-cpp-samples.md) ejemplo ilustra la implementación de una aplicación de contenedor de documento activo.  
  
## <a name="see-also"></a>Vea también  
 [MFC COM](../mfc/mfc-com.md)

