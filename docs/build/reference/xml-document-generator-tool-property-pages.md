---
title: Herramienta Generador de documentos XML (Páginas de propiedades)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: c99677d7fc53ae3343e15e54997fe0101322fbcf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827504"
---
# <a name="xml-document-generator-tool-property-pages"></a>Herramienta Generador de documentos XML (Páginas de propiedades)

La página de propiedades de la herramienta Generador de documentos XML expone la funcionalidad de xdcmake.exe. xdcmake.exe combina archivos .xdc en un archivo .xml cuando el código fuente contiene comentarios de documentación y se especifica [/doc (Procesar comentarios de documentación) (C/C++)](doc-process-documentation-comments-c-cpp.md). Vea [Etiquetas recomendadas para los comentarios de documentación](recommended-tags-for-documentation-comments-visual-cpp.md) para obtener información sobre cómo agregar comentarios de documentación al código fuente.

> [!NOTE]
>  Las opciones de xdcmake.exe en el entorno de desarrollo (las páginas de propiedades) difieren de las opciones cuando se usa xdcmake.exe en la línea de comandos. Para obtener información sobre cómo usar xdcmake.exe en la línea de comandos, vea [XDCMake (Referencia)](xdcmake-reference.md).

## <a name="uielement-list"></a>Lista de UIElement

- **Suprimir la pancarta de inicio**

   Se suprime el mensaje de copyright.

- **Archivos de documento adicionales**

   Directorios adicionales en los que quiere que el sistema del proyecto busque los archivos .xdc. xdcmake siempre buscará los archivos .xdc generados por el proyecto. Se pueden especificar varios directorios.

- **Archivo de documento de salida**

   El nombre y la ubicación de directorio del archivo de salida .xml. Consulte [macros comunes para propiedades y comandos de compilación](common-macros-for-build-commands-and-properties.md) para obtener información sobre el uso de macros para especificar ubicaciones de directorio.

- **Dependencias de la biblioteca de documentos**

   Si el proyecto tiene una dependencia de un proyecto .lib en la solución, los archivos .xdc del proyecto .lib se pueden procesar en los archivos .xml para el proyecto actual.

## <a name="see-also"></a>Vea también

[Referencia de página de propiedades de proyecto de C++](property-pages-visual-cpp.md)