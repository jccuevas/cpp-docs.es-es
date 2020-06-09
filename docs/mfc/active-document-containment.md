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
ms.openlocfilehash: 1c524d6890cd7b86bcae2c40d8c602e7b04e751b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623439"
---
# <a name="active-document-containment"></a>Contención de documentos activos

La contención de documentos activos es una tecnología que proporciona un único fotograma en el que trabajar con documentos, en lugar de obligarle a crear y usar varios marcos de aplicación para cada tipo de documento. Difiere de la tecnología básica de OLE en que OLE trabaja con objetos incrustados dentro de un documento compuesto en el que solo puede haber un elemento de contenido activo. Con la contención de documentos activos, se activa un documento completo (es decir, una aplicación completa, incluidos los menús asociados, las barras de herramientas, etc.) dentro del contexto de un solo fotograma.

La tecnología de contención de documentos activos se desarrolló originalmente para Microsoft Office implementar el enlazador de Office. Sin embargo, la tecnología es lo suficientemente flexible como para admitir contenedores de documentos activos distintos del enlazador de Office y puede admitir servidores de documentos distintos de Office y aplicaciones compatibles con Office.

La aplicación que hospeda documentos activos se denomina [contenedor de documentos activos](active-document-containers.md). Algunos ejemplos de estos contenedores son los Microsoft Office Binder o Microsoft Internet Explorer.

La contención de documentos activos se implementa como un conjunto de extensiones para documentos OLE, la tecnología de documentos compuestos de OLE. Las extensiones son interfaces adicionales que permiten que un objeto incrustado en contexto represente un documento completo en lugar de un único fragmento de contenido incrustado. Al igual que con los documentos OLE, la contención de documentos activos usa un contenedor que proporciona el espacio para mostrar para los documentos activos y los servidores que proporcionan la interfaz de usuario y las capacidades de manipulación para los propios documentos activos.

Un [servidor de documentos activo](active-document-servers.md) es una aplicación (como Word, Excel o PowerPoint) que admite una o varias clases de documentos activos, donde cada objeto admite las interfaces de extensión que permiten activar el objeto en un contenedor adecuado.

Un [documento activo](active-documents.md) (proporcionado desde un servidor de documentos activo como Word o Excel) es esencialmente un documento convencional y a escala completa que se incrusta como un objeto dentro de otro contenedor de documentos activos. A diferencia de los objetos incrustados, los documentos activos tienen un control total sobre sus páginas y la interfaz completa de la aplicación (con todos sus comandos y herramientas subyacentes) está disponible para que el usuario las edite.

Un documento activo se entiende mejor al distinguirlo de un objeto estándar OLE incrustado. Siguiendo la Convención OLE, un objeto incrustado es uno que se muestra dentro de la página del documento que lo posee y un contenedor OLE administra el documento. El contenedor almacena los datos del objeto incrustado con el resto del documento. Sin embargo, los objetos incrustados están limitados en que no controlan la página en la que aparecen.

Los usuarios de una aplicación contenedora de documentos activos pueden crear documentos activos (denominados secciones en el enlazador de Office) mediante sus aplicaciones favoritas (siempre que estas aplicaciones estén habilitadas como documentos activos), pero los usuarios pueden administrar el proyecto resultante como una sola entidad, que se puede asignar un nombre único, guardar, imprimir, etc. Del mismo modo, un usuario de un explorador de Internet puede tratar toda la red, así como los sistemas de archivos locales, como una única entidad de almacenamiento de documentos con la capacidad de examinar los documentos de ese almacenamiento desde una sola ubicación.

## <a name="sample-programs"></a>Programas de ejemplo

- En el ejemplo [MFCBIND](../overview/visual-cpp-samples.md) se muestra la implementación de una aplicación contenedora de documentos activos.

## <a name="see-also"></a>Consulte también

[MFC COM](mfc-com.md)
