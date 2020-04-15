---
title: 'Herencia de propiedades en proyectos de Visual Studio: C++'
description: Cómo funciona la herencia de propiedades en proyectos nativos (MSBuild) de Visual Studio C++.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328473"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Herencia de propiedades en proyectos de Visual Studio

El sistema de proyectos nativo de Visual Studio se basa en MSBuild. MSBuild define formatos de archivo y reglas para crear proyectos de cualquier tipo. Administra la mayor parte de la complejidad de la creación para múltiples configuraciones y plataformas. Le resultará útil entender cómo funciona. Esto es especialmente importante si desea definir configuraciones personalizadas. O bien, para crear conjuntos reutilizables de propiedades que puede compartir e importar en varios proyectos.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>El archivo .vcxproj, archivos .props y .targets

Las propiedades del proyecto se almacenan*`.vcxproj`* directamente *`.targets`* en *`.props`* el archivo de proyecto ( ) o en otros archivos que importa el archivo de proyecto y que proporcionan valores predeterminados. Para Visual Studio 2015, estos *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* archivos se encuentran en . Para Visual Studio 2017, estos *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* archivos *`<edition>`* se encuentran en , donde está instalada la edición de Visual Studio. En Visual Studio 2019, estos *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* archivos se encuentran en . Las propiedades también se *`.props`* almacenan en los archivos personalizados que puede agregar a su propio proyecto. Le recomendamos encarecidamente que NO edite esos archivos manualmente. En su lugar, use las páginas de propiedades del IDE para modificar todas las propiedades, especialmente las que participan en la herencia, a menos que tenga un conocimiento profundo de MSBuild.

Como se ha mostrado antes, se puede asignar otro valor a la misma propiedad para la misma configuración en estos archivos diferentes. Cuando se compila un proyecto, el motor de MSBuild evalúa el archivo de proyecto y todos los archivos importados en un orden bien definido (descrito a continuación). Al evaluar cada archivo, los valores de propiedad definidos en ese archivo invalidarán los valores existentes. Los valores que no se especifican se heredan de los archivos que se evaluaron anteriormente. Al establecer una propiedad con páginas de propiedades, también es importante prestar atención a dónde se establece. Si establece una propiedad en "X" en un *`.props`* archivo, pero la propiedad se establece en "Y" en el archivo de proyecto, el proyecto se compilará con la propiedad establecida en "Y". Si la misma propiedad se establece en "Z" *`.cpp`* en un elemento de proyecto, como un archivo, el motor de MSBuild usará el valor "Z".

Este es el árbol básico de herencia:

1. Configuración predeterminada del conjunto de herramientas CPP de MSBuild (.. •Archivos de programa, MSBuild, Microsoft.Cpp, v4.0, Microsoft.Cpp.Default.props, que es importado por el *`.vcxproj`* archivo.)

1. Hojas de propiedades

1. *`.vcxproj`* Archivo. (Puede invalidar la configuración predeterminada y de la hoja de propiedades).

1. Metadatos de elemento

> [!TIP]
> En una página de propiedades, una propiedad en **negrita** se define en el contexto actual. Se hereda una propiedad en fuente normal.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Visualización de un archivo de proyecto expandido con todos los valores importados

En ocasiones, es útil ver el archivo expandido para determinar cómo se hereda un valor de propiedad especificado. Para ver la versión ampliada, escriba el siguiente comando en un símbolo del sistema de Visual Studio. (Cambie los nombres de archivo de marcador de posición a los que desea usar).

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

Los archivos de proyecto expandidos pueden ser grandes y difíciles de entender a menos que esté familiarizado con MSBuild. A continuación se muestra la estructura básica de un archivo de proyecto:

1. Propiedades fundamentales del proyecto, que no se exponen en el IDE.

1. Importación *`Microsoft.cpp.default.props`* de , que define algunas propiedades básicas independientes del conjunto de herramientas.

1. Página de propiedades de configuración global (expuestas como **PlatformToolset** y propiedades predeterminadas de **Proyecto** en la página **Configuración general**. Estas propiedades determinan en qué conjunto de *`Microsoft.cpp.props`* herramientas y en las hojas de propiedades intrínsecas se importan en el paso siguiente.

1. Importación *`Microsoft.cpp.props`* de , que establece la mayoría de los valores predeterminados del proyecto.

1. Importación de todas *`.user`* las hojas de propiedades, incluidos los archivos. Estas hojas de propiedades pueden reemplazar todo excepto las propiedades predeterminadas **PlatformToolset** y **Project**.

1. El resto de las propiedades de configuración del proyecto. Estos valores pueden invalidar lo que estaba establecido en las hojas de propiedades.

1. Elementos (archivos), junto con sus metadatos. Estos elementos son siempre la última palabra de las reglas de evaluación de MSBuild, incluso si se producen antes de otras propiedades e importaciones.

Para obtener más información, vea [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configuraciones de compilación

Una configuración es solo un grupo arbitrario de propiedades a las que se asigna un nombre. Visual Studio proporciona configuraciones de depuración y versión. Cada uno establece varias propiedades de forma adecuada para una compilación de depuración o una compilación de versión. Puede usar **Configuration Manager** para definir configuraciones personalizadas. Son una manera conveniente de agrupar propiedades para un sabor específico de construcción.

Para tener una mejor idea de las configuraciones de compilación, abra **el Administrador de propiedades**. Puede abrirlo seleccionando **Ver > Administrador** de propiedades o Ver > Otros > Administrador de propiedades de **Windows,** en función de la configuración. **Property Manager** tiene nodos para cada configuración y par de plataformas en el proyecto. En cada uno de estos nodos*`.props`* hay nodos para hojas de propiedades (archivos) que establecen algunas propiedades específicas para esa configuración.

![Administrador de propiedades](media/property-manager.png "Administrador de propiedades")

Por ejemplo, puede ir al panel General en las páginas de propiedades. Cambie la propiedad Conjunto de caracteres a "No establecido" en lugar de "Usar Unicode" y, a continuación, haga clic en **Aceptar**. El Administrador de propiedades ahora no muestra ninguna hoja de propiedades **de soporte Unicode.** Se quita para la configuración actual, pero todavía está allí para otras configuraciones.

Para más información sobre el Administrador de propiedades y las hojas de propiedades, vea [Compartir o volver a usar la configuración del proyecto de Visual Studio - C++](create-reusable-property-configurations.md).

> [!TIP]
> El *`.user`* archivo es una característica heredada. Le recomendamos que lo elimine, para mantener las propiedades correctamente agrupadas según la configuración y la plataforma.
