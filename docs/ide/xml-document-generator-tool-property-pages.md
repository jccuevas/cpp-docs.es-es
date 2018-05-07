---
title: Páginas de propiedades de herramienta de generador de documento XML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 772e9dc6a296873ef27171676ebca0c185c1771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-generator-tool-property-pages"></a>Herramienta Generador de documentos XML (Páginas de propiedades)
La página de propiedades de la herramienta Generador de documentos XML expone la funcionalidad de xdcmake.exe. xdcmake.exe combina archivos .xdc en un archivo .xml cuando el código fuente contiene comentarios de documentación y [/doc (procesar comentarios de documentación) (C/C ++)](../build/reference/doc-process-documentation-comments-c-cpp.md) se especifica,. Vea [etiquetas recomendadas para comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) para obtener información sobre cómo agregar comentarios de documentación en código fuente.  
  
> [!NOTE]
>  Opciones de XDCMake.exe en el entorno de desarrollo (páginas de propiedades) difieren de las opciones cuando se use xdcmake.exe en la línea de comandos. Para obtener información sobre cómo utilizar xdcmake.exe en la línea de comandos, consulte [XDCMake Reference](../ide/xdcmake-reference.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Suprimir el titular de inicio**  
 Suprimir mensaje de copyright.  
  
 **Archivos de documento adicionales**  
 Directorios adicionales en el que desea que el sistema del proyecto para que busque archivos .xdc. XDCMake siempre buscará archivos .xdc generados por el proyecto. Se pueden especificar varios directorios.  
  
 **Archivo de documento de salida**  
 La ubicación de directorio y nombre del archivo de salida XML. Vea [comunes Macros para propiedades y comandos de generación](../ide/common-macros-for-build-commands-and-properties.md) para obtener información sobre cómo utilizar macros para especificar ubicaciones de directorio.  
  
 **Dependencias de biblioteca de documentos**  
 Si el proyecto tiene una dependencia de un proyecto .lib en la solución, puede procesar archivos .xdc del proyecto .lib en los archivos .xml para el proyecto actual.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)