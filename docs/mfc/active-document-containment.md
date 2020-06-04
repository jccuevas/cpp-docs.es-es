---
title: Contención de documentos activos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: dc13384454c4732d3efbf99def5d05dd4f2d44aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394973"
---
# <a name="active-document-containment"></a>Contención de documentos activos

Contención de documentos activos es una tecnología que proporciona un marco único en la que se va a trabajar con documentos, en lugar de obligarle a crear y usar varios marcos de aplicación para cada tipo de documento. Difiere de la tecnología OLE básica en que OLE funciona con objetos incrustados dentro de un documento compuesto en el que solo una parte única del contenido puede estar activa. Con la contención de documentos activos, puede activar un documento completo (es decir, una aplicación completa, incluidos menús asociados, las barras de herramientas etc.) dentro del contexto de un solo fotograma.

La tecnología de contención de documentos activos se desarrolló originalmente para que Microsoft Office implementar el cuaderno de Office. Sin embargo, la tecnología es lo suficientemente flexible como para admitir los contenedores de documentos activos que no sea el cuaderno de Office y puede admitir servidores de documentos que no sean aplicaciones compatibles con Office y Office.

Se llama a la aplicación que hospeda los documentos activos un [contenedor de documentos activos](../mfc/active-document-containers.md). Ejemplos de estos contenedores son el cuaderno de Microsoft Office o Microsoft Internet Explorer.

Contención de documentos activos se implementa como un conjunto de extensiones OLE de documentos, la tecnología de documento compuesto de OLE. Las extensiones son interfaces adicionales que permiten que un objeto insertable, en lugar de representar un documento completo en lugar de un único fragmento de contenido incrustado. Al igual que con los documentos OLE, contención de documentos activos utiliza un contenedor que proporciona el espacio de visualización de documentos activos y los servidores que proporcionan funciones de interfaz y la manipulación de usuario para los documentos activos.

Un [servidor de documentos activos](../mfc/active-document-servers.md) es una aplicación (por ejemplo, Word, Excel o PowerPoint) que admite una o más clases de documento activo, donde cada objeto en sí es compatible con las interfaces de extensión que permiten el objeto que debe activarse en un contenedor adecuado.

Un [documento activo](../mfc/active-documents.md) (proporcionado por un servidor de documentos activos como Word o Excel) es esencialmente un documento convencional que se incrusta como un objeto en otro contenedor de documentos activos. A diferencia de los objetos incrustados, documentos activos tienen control total sobre sus páginas y toda la interfaz de la aplicación (con todas sus subyacente comandos y herramientas) está disponible para el usuario para editarlos.

Un documento activo se entiende mejor comparándolo con un objeto OLE incrustado estándar. Seguir la convención OLE, un objeto incrustado es aquella que se muestra en la página del documento que es su propietario y el documento está administrado por un contenedor OLE. El contenedor almacena los datos del objeto incrustado con el resto del documento. Sin embargo, los objetos incrustados están limitados porque no controlan la página en el que aparecen.

Los usuarios de una aplicación de contenedor de documentos activos pueden crear documentos activos (denominados secciones en el cuaderno de Office) con sus aplicaciones favoritas (siempre que estas aplicaciones admiten documentos activos), pero los usuarios pueden administrar el proyecto resultante como una una entidad única, que puede ser nombra, guardar, imprimir, y así sucesivamente. En la misma manera, un usuario de un explorador de Internet puede tratar la toda la red, así como sistemas de archivos locales, como una entidad de almacenamiento de documento único con la capacidad de examinar los documentos en que el almacenamiento desde una sola ubicación.

## <a name="sample-programs"></a>Programas de ejemplo

- El [MFCBIND](../overview/visual-cpp-samples.md) ejemplo ilustra la implementación de una aplicación de contenedor de documentos activos.

## <a name="see-also"></a>Vea también

[MFC COM](../mfc/mfc-com.md)
