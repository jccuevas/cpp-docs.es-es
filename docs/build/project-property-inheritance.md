---
title: 'Herencia de propiedades en proyectos de Visual Studio: C++'
description: Cómo funciona la herencia de propiedades en proyectos de Visual Studio C++ nativos (MSBuild).
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328473"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Herencia de propiedades en proyectos de Visual Studio

El sistema de proyectos nativos de Visual Studio se basa en MSBuild. MSBuild define los formatos de archivo y las reglas para compilar proyectos de cualquier tipo. Administra la mayor parte de la complejidad de la creación de varias configuraciones y plataformas. Le resultará útil entender cómo funciona. Esto es especialmente importante si quiere definir configuraciones personalizadas. O bien, si quiere crear conjuntos de propiedades reutilizables que se pueden compartir e importar en varios proyectos.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>El archivo .vcxproj, archivos .props y .targets

Las propiedades del proyecto se almacenan directamente en el archivo de proyecto ( *`.vcxproj`* ) o en otros archivos *`.targets`* o *`.props`* que el archivo de proyecto importa y que proporcionan los valores predeterminados. En Visual Studio 2015, estos archivos se encuentran en *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* . En Visual Studio 2017, estos archivos se encuentran en *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* , donde *`<edition>`* es la edición de Visual Studio instalada. En Visual Studio 2019, estos archivos se encuentran en *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* . Las propiedades también se almacenan en los archivos *`.props`* personalizados que es posible que se agreguen a un proyecto propio. Se recomienda encarecidamente no editar esos archivos de forma manual. En su lugar, use las páginas de propiedades del IDE para modificar todas las propiedades, en especial las que participan en la herencia, a menos que se tenga un gran conocimiento de MSBuild.

Como se ha mostrado antes, se puede asignar otro valor a la misma propiedad para la misma configuración en estos archivos diferentes. Cuando se compila un proyecto, el motor de MSBuild evalúa el archivo de proyecto y todos los archivos importados en un orden bien definido (descrito a continuación). Al evaluar cada archivo, los valores de propiedad definidos en ese archivo invalidarán los valores existentes. Los valores que no se especifiquen se heredan de los archivos que se evaluaron anteriormente. Cuando se establece una propiedad con páginas de propiedades, también es importante prestar atención a dónde se establece. Si se establece una propiedad en "X" en un archivo *`.props`* , pero se establece en "Y" en el archivo de proyecto, el proyecto se compilará con la propiedad establecida en "Y". Si la misma propiedad se establece en "Z" en un elemento de proyecto, como un archivo *`.cpp`* , el motor de MSBuild usará el valor de "Z".

Este es el árbol básico de herencia:

1. Configuración predeterminada del conjunto de herramientas de MSBuild CPP (..\Archivos de programa\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, que importa el archivo *`.vcxproj`* ).

1. Hojas de propiedades

1. Archivo *`.vcxproj`* . (Puede invalidar la configuración predeterminada y de la hoja de propiedades).

1. Metadatos de elemento

> [!TIP]
> En una página de propiedades, una propiedad en **negrita** se define en el contexto actual. Se hereda una propiedad en fuente normal.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Visualización de un archivo de proyecto expandido con todos los valores importados

En ocasiones, es útil ver el archivo expandido para determinar cómo se hereda un valor de propiedad especificado. Para ver la versión ampliada, escriba el siguiente comando en un símbolo del sistema de Visual Studio. (Cambie los nombres de archivo de marcador de posición a los que desea usar).

> **msbuild /pp:** _temp_ **.txt** _myapp_ **.vcxproj**

Los archivos de proyecto expandidos pueden ser de gran tamaño y difíciles de comprender a menos que esté familiarizado con MSBuild. A continuación se muestra la estructura básica de un archivo de proyecto:

1. Propiedades fundamentales del proyecto que no se exponen en el IDE.

1. Importación de *`Microsoft.cpp.default.props`* , que define algunas propiedades básicas independientes del conjunto de herramientas.

1. Página de propiedades de configuración global (expuestas como **PlatformToolset** y propiedades predeterminadas de **Proyecto** en la página **Configuración general**. Estas propiedades determinan qué conjunto de herramientas y hojas de propiedades intrínsecas se importan en *`Microsoft.cpp.props`* en el paso siguiente.

1. Importación de *`Microsoft.cpp.props`* , que establece la mayoría de los valores predeterminados del proyecto.

1. Importación de todas las hojas de propiedades, incluidos los archivos *`.user`* . Estas hojas de propiedades pueden reemplazar todo excepto las propiedades predeterminadas **PlatformToolset** y **Project**.

1. El resto de propiedades de configuración del proyecto. Estos valores pueden invalidar lo que estaba establecido en las hojas de propiedades.

1. Elementos (archivos), junto con sus metadatos. Estos elementos son siempre la última palabra en las reglas de evaluación de MSBuild, aunque se produzcan antes de otras propiedades e importaciones.

Para obtener más información, consulte [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configuraciones de compilación

Una configuración es solo un grupo arbitrario de propiedades a las que se asigna un nombre. Visual Studio proporciona configuraciones de depuración y versión. Cada una determina varias propiedades de forma adecuada para una compilación de depuración o una compilación de versión. Puede usar el **Administrador de configuración** para configurar estas propiedades. Son una manera cómoda de agrupar las propiedades de un tipo específico de compilación.

Para obtener más información sobre las configuraciones de compilación, abra el **Administrador de propiedades**. Para abrirlo, elija **Ver > Administrador de propiedades** o **Ver > Otras ventanas > Administrador de propiedades**, dependiendo de la configuración. El **Administrador de propiedades** tiene nodos para cada par de configuración y plataforma del proyecto. En cada uno de estos nodos hay otros nodos para las hojas de propiedades (los archivos *`.props`* ) que establecen algunas propiedades específicas para esa configuración.

![Administrador de propiedades](media/property-manager.png "Administrador de propiedades")

Por ejemplo, puede ir al panel General en las páginas de propiedades. Cambie la propiedad Juego de caracteres a "Sin establecer" en lugar de "Usar Unicode" y, a continuación, haga clic en **Aceptar**. El Administrador de propiedades ahora ya no muestra la hoja de propiedades **Compatibilidad con Unicode**. Se quita para la configuración actual, pero todavía existe para otras configuraciones.

Para más información sobre el Administrador de propiedades y las hojas de propiedades, vea [Compartir o volver a usar la configuración del proyecto de Visual Studio - C++](create-reusable-property-configurations.md).

> [!TIP]
> El archivo *`.user`* es una característica heredada. Se recomienda eliminarlo para conservar las propiedades agrupadas de forma correcta según la configuración y la plataforma.
