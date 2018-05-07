---
title: Documentación XML (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee19c51c04fa32ab3c2f1810bb963b22ec7e890
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="xml-documentation-visual-c"></a>Documentación XML (Visual C++)
En Visual C++, puede agregar comentarios al código fuente que se procesará en un archivo XML. Este archivo puede ser, a continuación, la entrada a un proceso que crea la documentación de las clases en el código.  
  
 En un archivo de código de Visual C++, los comentarios de documentación XML deben encontrarse directamente antes de una definición de tipo o método. Los comentarios se pueden usar para rellenar la información sobre datos de Intellisense QuickInfo en los escenarios siguientes:  
  
1.  Cuando el código se compila como un componente en tiempo de ejecución de Windows con un archivo .winmd que lo acompaña  
  
2.  Cuando el código fuente se incluye en el proyecto actual  
  
3.  en una biblioteca cuyo declaraciones de tipos y las implementaciones se encuentran en el mismo archivo de encabezado  
  
> [!NOTE]
>  En la versión actual, los comentarios de código no se procesan en plantillas o cualquier elemento que contiene un tipo de plantilla (por ejemplo, una función que toma un parámetro como una plantilla). Agregar estos comentarios se producirá un comportamiento indefinido.  
  
 Para obtener más información sobre cómo crear un archivo .xml con los comentarios de documentación, vea los temas siguientes.  
  
|Para buscar información sobre|Vea|  
|---------------------------|---------|  
|Las opciones del compilador para usar|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|Funcionalidad de etiquetas que se puede utilizar para proporcionar habitualmente utilizan en la documentación|[Etiquetas recomendadas para los comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|Las cadenas de identificador que el compilador genera para identificar las construcciones en el código|[Procesar el archivo .xml](../ide/dot-xml-file-processing.md)|  
|Cómo delimitar etiquetas de documentación|[Delimitadores para etiquetas de documentación en Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|Generar un archivo .xml de uno o más archivos .xdc.|[XDCMake (Referencia)](../ide/xdcmake-reference.md)|  
|Vínculos a información acerca de XML a medida que se relación con las áreas de características de Visual Studio|[XML en Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|  
  
 Si tiene que colocar los caracteres especiales de XML en el texto de un comentario de documentación, debe usar entidades XML o una sección CDATA.  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)