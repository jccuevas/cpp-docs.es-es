---
title: Documentación XML (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: c25c54e81bb9c10fc871a2abc178f57e661ae4e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335731"
---
# <a name="xml-documentation-visual-c"></a>Documentación XML (Visual C++)

En Visual C++, se pueden agregar comentarios al código fuente que se procesarán en un archivo .xml. Después, este archivo puede ser la entrada para un proceso que crea la documentación para las clases del código.

En un archivo de código de Visual C++, los comentarios de documentación XML deben encontrarse directamente antes de una definición de tipo o método. Los comentarios se pueden usar para rellenar la información sobre datos de Información rápida de IntelliSense en los escenarios siguientes:

1. Cuando el código se compila como un componente de Windows Runtime con un archivo .winmd que lo acompaña.

1. Cuando el código fuente se incluye en el proyecto actual.

1. En una biblioteca cuyas declaraciones e implementaciones de tipos se encuentran en el mismo archivo de encabezado.

> [!NOTE]
> En la versión actual, los comentarios de código no se procesan en plantillas o ningún elemento que contenga un tipo de plantilla (por ejemplo, una función que toma un parámetro como una plantilla). Agregar estos comentarios producirá un comportamiento no definido.

Para obtener más información sobre cómo crear un archivo .xml con los comentarios de documentación, vea los temas siguientes.

|Para información acerca de|Vea|
|---------------------------|---------|
|Las opciones del compilador que se van a usar.|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Las etiquetas que se pueden usar para proporcionar funciones de uso general en la documentación.|[Etiquetas recomendadas para comentarios de documentación](recommended-tags-for-documentation-comments-visual-cpp.md)|
|Las cadenas de identificador que el compilador genera para identificar las construcciones en el código.|[Procesamiento del archivo .xml](dot-xml-file-processing.md)|
|Cómo delimitar las etiquetas de documentación|[Delimitadores para etiquetas de documentación en Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Generar un archivo .xml a partir de uno o más archivos .xdc.|[XDCMake (Referencia)](xdcmake-reference.md)|
|Vínculos a información sobre XML en relación con las áreas de características de Visual Studio|[XML en Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Si tiene que colocar caracteres especiales de XML en el texto de un comentario de documentación, debe usar entidades XML o una sección CDATA.

## <a name="see-also"></a>Consulte también

[Extensiones de componentes para plataformas de tiempo de ejecución](../../extensions/component-extensions-for-runtime-platforms.md)
