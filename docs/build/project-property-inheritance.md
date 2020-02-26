---
title: 'Herencia de propiedades en proyectos de Visual Studio: C++'
description: Cómo funciona la herencia de propiedades en proyectos de Visual Studio C++ nativos (MSBuild).
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 2032ab63c7d278a080742dba8d8d0c6c3ed7a094
ms.sourcegitcommit: 9a63e9b36d5e7fb13eab15c2c35bedad4fb03ade
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600019"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Herencia de propiedades en proyectos de Visual Studio

El sistema de proyectos nativo de Visual Studio se basa en MSBuild. MSBuild define los formatos de archivo y las reglas para compilar proyectos de cualquier tipo. Administra la mayor parte de la complejidad de la creación de varias configuraciones y plataformas. Le resultará útil entender cómo funciona. Esto es especialmente importante si desea definir configuraciones personalizadas. O bien, para crear conjuntos de propiedades reutilizables que se pueden compartir e importar en varios proyectos.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>El archivo .vcxproj, archivos .props y .targets

Las propiedades del proyecto se almacenan directamente en el archivo de proyecto ( *`.vcxproj`* ) o en otros archivos *`.targets`* o *`.props`* que el archivo de proyecto importa y que suministran los valores predeterminados. En Visual Studio 2015, estos archivos se encuentran en *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* . En Visual Studio 2017, estos archivos se encuentran en *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* , donde *`<edition>`* es la edición de Visual Studio instalada. En Visual Studio 2019, estos archivos se encuentran en *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* . Las propiedades también se almacenan en los archivos de *`.props`* personalizados que puede Agregar a su propio proyecto. Le recomendamos encarecidamente que no edite los archivos manualmente. En su lugar, use las páginas de propiedades del IDE para modificar todas las propiedades, especialmente las que participan en la herencia, a menos que tenga conocimientos profundos de MSBuild.

Como se ha mostrado antes, se puede asignar otro valor a la misma propiedad para la misma configuración en estos archivos diferentes. Cuando se compila un proyecto, el motor de MSBuild evalúa el archivo de proyecto y todos los archivos importados en un orden bien definido (descrito a continuación). Al evaluar cada archivo, los valores de propiedad definidos en ese archivo invalidarán los valores existentes. Los valores que no se especifican se heredan de los archivos que se evaluaron anteriormente. Cuando se establece una propiedad con páginas de propiedades, también es importante prestar atención a la ubicación en la que se establece. Si establece una propiedad en "X" en un archivo *`.props`* , pero la propiedad se establece en "y" en el archivo de proyecto, el proyecto se compilará con la propiedad establecida en "y". Si la misma propiedad se establece en "Z" en un elemento de proyecto, como un archivo *`.cpp`* , el motor de MSBuild usará el valor "Z".

Este es el árbol básico de herencia:

1. Configuración predeterminada del conjunto de herramientas de MSBuild CPP (.. \Archivos de Programa\msbuild\microsoft.cpp\v4.0\microsoft.cpp.default.props, que importa el archivo *`.vcxproj`* ).

1. Hojas de propiedades

1. *`.vcxproj`* archivo. (Puede invalidar la configuración predeterminada y de la hoja de propiedades).

1. Metadatos de elemento

> [!TIP]
> En una página de propiedades, una propiedad en **negrita** se define en el contexto actual. Se hereda una propiedad en fuente normal.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Visualización de un archivo de proyecto expandido con todos los valores importados

En ocasiones, es útil ver el archivo expandido para determinar cómo se hereda un valor de propiedad especificado. Para ver la versión ampliada, escriba el siguiente comando en un símbolo del sistema de Visual Studio. (Cambie los nombres de archivo de marcador de posición a los que desea usar).

> **msbuild/PP:** _temp_ **. txt** _MyApp_ **. vcxproj**

Los archivos de proyecto expandidos pueden ser grandes y difíciles de comprender a menos que esté familiarizado con MSBuild. A continuación se muestra la estructura básica de un archivo de proyecto:

1. Propiedades fundamentales del proyecto, que no se exponen en el IDE.

1. Importación de *`Microsoft.cpp.default.props`* , que define algunas propiedades básicas independientes del conjunto de herramientas.

1. Página de propiedades de configuración global (expuestas como **PlatformToolset** y propiedades predeterminadas de **Proyecto** en la página **Configuración general**. Estas propiedades determinan qué conjunto de herramientas y las hojas de propiedades intrínsecas se importan en *`Microsoft.cpp.props`* en el paso siguiente.

1. Importación de *`Microsoft.cpp.props`* , que establece la mayoría de los valores predeterminados del proyecto.

1. Importación de todas las hojas de propiedades, incluidos los archivos *`.user`* . Estas hojas de propiedades pueden reemplazar todo excepto las propiedades predeterminadas **PlatformToolset** y **Project**.

1. El resto de las propiedades de configuración del proyecto. Estos valores pueden invalidar lo que estaba establecido en las hojas de propiedades.

1. Elementos (archivos), junto con sus metadatos. Estos elementos siempre son la última palabra en las reglas de evaluación de MSBuild, aunque se produzcan antes de otras propiedades e importaciones.

Para obtener más información, consulte [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configuraciones de compilación

Una configuración es solo un grupo arbitrario de propiedades a las que se asigna un nombre. Visual Studio proporciona configuraciones de depuración y lanzamiento. Cada uno establece varias propiedades de forma adecuada para una compilación de depuración o una compilación de versión. Puede utilizar la **Configuration Manager** para definir configuraciones personalizadas. Son una manera cómoda de agrupar las propiedades de un tipo específico de compilación.

Para obtener una idea más clara de las configuraciones de compilación, Abra **Administrador de propiedades**. Para abrirlo, seleccione **ver > Administrador de propiedades** o **Ver > otras ventanas > Administrador de propiedades**, en función de la configuración. **Administrador de propiedades** tiene nodos para cada par de configuración y plataforma del proyecto. En cada uno de estos nodos hay nodos para hojas de propiedades (archivos *`.props`* ) que establecen algunas propiedades específicas para esa configuración.

![Administrador de propiedades](media/property-manager.png "Administrador de propiedades")

Por ejemplo, puede ir al panel General en las páginas de propiedades. Cambie la propiedad juego de caracteres a "sin establecer" en lugar de "usar Unicode" y, a continuación, haga clic en **Aceptar**. En el Administrador de propiedades ahora se muestra la hoja de propiedades **compatibilidad con Unicode** . Se quita para la configuración actual, pero todavía existe para otras configuraciones.

Para más información sobre el Administrador de propiedades y las hojas de propiedades, vea [Compartir o volver a usar la configuración del proyecto de Visual Studio - C++](create-reusable-property-configurations.md).

> [!TIP]
> El archivo *`.user`* es una característica heredada. Se recomienda eliminarlo para mantener las propiedades correctamente agrupadas según la configuración y la plataforma.
