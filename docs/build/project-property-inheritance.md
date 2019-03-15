---
title: 'Herencia de propiedades en proyectos de Visual Studio: C++'
ms.date: 12/10/2018
helpviewer_keywords:
- Visual C++ projects, property inheritance
ms.openlocfilehash: edd6d3bf82f7a13cf6687abeba3758dcceca5e84
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827274"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Herencia de propiedades en proyectos de Visual Studio

El sistema del proyecto de Visual Studio se basa en MSBuild, que define los formatos de archivo y las reglas para la creación de proyectos de cualquier tipo. MSBuild administra gran parte de la complejidad de la compilación para varias plataformas y configuraciones, pero debe comprender un poco su funcionamiento. Esto es especialmente importante si quiere definir configuraciones personalizadas o crear conjuntos reutilizables de propiedades que pueda compartir e importar en varios proyectos.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>El archivo .vcxproj, archivos .props y .targets archivos

Propiedades del proyecto se almacenan directamente en el archivo de proyecto (*.vcxproj) o en otros archivos .targets o .props que las importaciones del archivo de proyecto y que proporcionan los valores predeterminados. Para Visual Studio 2015, estos archivos se encuentran en **\Archivos de programa (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Para Visual Studio 2017, estos archivos se encuentran en **\\Archivos de programa (x86)\\Microsoft Visual Studio\\2017\\_edición_\\Common7\\IDE\\VC\\VCTargets**, donde _edición_ es la edición de Visual Studio instalada. Las propiedades también se almacenan en los archivos .props personalizados que es posible que se agreguen a un proyecto propio. Se recomienda encarecidamente NO modificar esos archivos de forma manual y, en su lugar, usar las páginas de propiedades del IDE para modificar todas las propiedades, en especial las que participan en la herencia, a menos que se tenga un conocimiento excelente de MSBuild.

Como se muestra anteriormente, la misma propiedad para la misma configuración puede asignarse un valor distinto en estos archivos diferentes. Cuando se compila un proyecto, el motor de MSBuild evalúa el archivo de proyecto y todos los archivos importados en un orden bien definido (descrito a continuación). Al evaluar cada archivo, los valores de propiedad definidos en ese archivo invalidarán los valores existentes. Los valores que no se especifiquen se heredan de los archivos que se evaluaron anteriormente. Por tanto, cuando se establece una propiedad con las páginas de propiedades, también es importante prestar atención a dónde se establece. Si se establece una propiedad en "X" en un archivo .props, pero se establece en "Y" en el archivo de proyecto, el proyecto se compilará con la propiedad establecida en "Y". Si la misma propiedad se establece en "Z" en un elemento de proyecto, como un archivo .cpp, el motor de MSBuild usará el valor de "Z". 

Este es el árbol básico de herencia:

1. Configuración predeterminada del conjunto de herramientas de MSBuild CPP (..\Archivos de programa\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, que importa el archivo .vcxproj).

2. Hojas de propiedades

3. Archivo .vcxproj. (Puede invalidar la configuración predeterminada y de la hoja de propiedades).

4. Metadatos de elemento

> [!TIP]
> En una página de propiedades, una propiedad en `bold` se define en el contexto actual. Se hereda una propiedad en fuente normal.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Ver un archivo de proyecto expandidos con todos los valores importados

En ocasiones, es útil ver el archivo expandido para determinar cómo se hereda un valor de propiedad especificado. Para ver la versión ampliada, escriba el siguiente comando en un símbolo del sistema de Visual Studio. (Cambie los nombres de archivo de marcador de posición a los que desea usar).

**msbuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

Los archivos de proyecto expandidos pueden ser de gran tamaño y difíciles de comprender a menos que esté familiarizado con MSBuild. A continuación se muestra la estructura básica de un archivo de proyecto:

1. Propiedades fundamentales del proyecto que no se exponen en el IDE.

2. Importación de Microsoft.cpp.default.props, que define algunas propiedades básicas independientes del conjunto de herramientas.

3. Página de propiedades de configuración global (expuestas como **PlatformToolset** y propiedades predeterminadas de **Proyecto** en la página **Configuración general**. Estas propiedades determinan qué conjunto de herramientas y hojas de propiedades intrínsecas se importan en Microsoft.cpp.props en el paso siguiente.

4. Importación de Microsoft.cpp.props, que establece la mayoría de los valores predeterminados del proyecto.

5. Importación de todas las hojas de propiedades, incluidos los archivos .user. Estas hojas de propiedades pueden reemplazar todo excepto las propiedades predeterminadas **PlatformToolset** y **Project**.

6. El resto de propiedades de configuración del proyecto. Estos valores pueden invalidar lo que estaba establecido en las hojas de propiedades.

7. Elementos (archivos), junto con sus metadatos. Estas son siempre la última palabra en las reglas de evaluación de MSBuild, aunque se produzcan antes de otras propiedades e importaciones.

Para obtener más información, consulte [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Configuraciones de compilación

Una configuración es solo un grupo arbitrario de propiedades a las que se asigna un nombre. Visual Studio proporciona configuraciones de depuración y versión, y cada una establece varias propiedades de forma adecuada para una compilación de depuración o de versión. Se puede usar el **Administrador de configuración** para definir configuraciones personalizadas como una manera cómoda de agrupar propiedades para un tipo de compilación específico. 

Para obtener una mejor idea de las configuraciones de compilación, abra **Administrador de propiedades** eligiendo **vista &#124; Administrador de propiedades** o **vista &#124; Other Windows &#124; Administrador de propiedades**  dependiendo de su configuración. **Administrador de propiedades** tiene nodos para cada par de configuración/plataforma en el proyecto. En cada uno de estos nodos hay nodos para las hojas de propiedades (los archivos .props) que establecen algunas propiedades específicas para esa configuración.

![Administrador de propiedades](media/property-manager.png "Property Manager")

Si ir al panel General de las páginas de propiedades y establezca la propiedad juego de caracteres a "Sin establecer" en lugar de "Uso de Unicode" y haga clic en **Aceptar**, Administrador de propiedades mostrará ningún **compatibilidad con Unicode** hoja de propiedades la configuración actual, pero se seguirá allí para otras configuraciones.

Para obtener más información sobre el Administrador de propiedades y hojas de propiedades, vea [configuraciones de proyecto de Visual Studio C++ del recurso compartido o resuse](create-reusable-property-configurations.md).

> [!TIP]
> El archivo .user es una característica heredada y se recomienda eliminarlo para conservar las propiedades agrupadas de forma correcta según la configuración y la plataforma.



