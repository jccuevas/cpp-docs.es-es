---
title: "Páginas de propiedades (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.NotAProp.Edit
dev_langs: C++
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0c342148266dff9551d2705f8095250daf2b096
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="property-pages-visual-c"></a>Páginas de propiedades (Visual C++)

Con las páginas de propiedades, puede especificar la configuración de los proyectos de Visual Studio. Para abrir el **páginas de propiedades** proyecto de cuadro de diálogo de Visual Studio, en el **proyecto** menú, elija **propiedades**.

Puede especificar la configuración del proyecto para que se aplique a todas las configuraciones de compilación o bien puede especificar propiedades de proyecto diferentes para cada configuración de compilación. Por ejemplo, puede especificar ciertos valores para la configuración de versión y otros para la configuración de depuración.

No todas las páginas disponibles se muestran necesariamente en el **páginas de propiedades** cuadro de diálogo. Las páginas que se muestran dependen de los tipos de archivo del proyecto.

Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).

Para los proyectos de distinta de Windows, vea [referencia de página de propiedades de C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Propiedades predeterminadas frente a propiedades modificadas

Cuando se usa el **nuevo proyecto** cuadro de diálogo para crear un proyecto, Visual Studio utiliza la plantilla de proyecto especificada para inicializar las propiedades del proyecto. Por lo tanto, los valores de las propiedades de la plantilla pueden considerarse como valores predeterminados para ese tipo de proyecto. En otros tipos de proyecto, las propiedades pueden tener diferentes valores predeterminados.

Un valor de propiedad de proyecto aparece en negrita si se ha modificado. Una propiedad de proyecto puede modificarse por las razones siguientes:

- El Asistente para aplicaciones cambia la propiedad porque necesita un valor de propiedad diferente al que se ha especificado en la plantilla de proyecto.

- Especifique un valor de propiedad distinto en el **nuevo proyecto** cuadro de diálogo.

- El usuario especifica un valor de propiedad distinto en una página de propiedades de proyecto.

> [!TIP]
> Para ver el conjunto final de los valores de propiedad que utiliza MSBuild para compilar el proyecto, examine el archivo de resultados del preprocesador, que puede generar mediante el uso de esta línea de comandos: **MSBuild / preprocesamiento:** *preprocessor_output_ nombre de archivo*<sub>opt</sub> *project_filename*<sub>participar</sub>

## <a name="resetting-properties"></a>Restablecer propiedades

Al ver el **páginas de propiedades** cuadro de diálogo para un proyecto y el nodo del proyecto está seleccionado en **el Explorador de soluciones**, para muchas propiedades, puede seleccionar **heredar de primario o un proyecto los valores predeterminados** o modificar el valor de otra manera.

Al ver el **páginas de propiedades** está seleccionado el cuadro de diálogo para un proyecto y un archivo en **el Explorador de soluciones**, para muchas propiedades, puede seleccionar **heredar de primario o valores pred.** o modificar el valor de otra manera. Sin embargo, si el proyecto contiene muchos archivos que tienen valores de propiedad que difieren de los valores predeterminados del proyecto, se tardará más tiempo en compilarlo.

> [!TIP]
> Para actualizar la **páginas de propiedades** cuadro de diálogo para que muestre las selecciones más recientes, elija **aplicar**.

La mayoría de los valores predeterminados del proyecto son valores predeterminados del sistema (plataforma). Algunos valores predeterminados del proyecto derivan de las hojas de estilos que se aplican al actualizar las propiedades en el **valores predeterminados del proyecto** sección de la **General** página de propiedades de configuración para el proyecto. Para obtener más información, consulte [página de propiedades General (proyecto)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Especificar valores definidos por el usuario

Debe definir el valor de algunas propiedades. Un valor definido por el usuario puede contener uno o más caracteres alfanuméricos o nombres de macro de archivo de proyecto. Algunas de estas propiedades pueden tomar un único valor definido por el usuario, pero otras pueden tomar una lista delimitada por puntos y coma de varios valores.

Para especificar un valor definido por el usuario para una propiedad, o una lista si la propiedad puede tomar varios valores definidos por el usuario, en la columna situada a la derecha del nombre de la propiedad, realice una de las siguientes acciones:

- Escriba el valor o la lista de valores.

- Elija la flecha de lista desplegable. Si **editar** está disponible, selecciónelo y, a continuación, en el cuadro de texto, escriba el valor o una lista de valores. Un medio alternativo de especificar una lista es escribir cada valor en una línea independiente del cuadro de texto. En la página de propiedades, los valores se mostrarán como una lista delimitada por puntos y coma.

   Para insertar una macro de archivo de proyecto como un valor, elija **Macros** y, a continuación, haga doble clic en el nombre de la macro.

- Elija la flecha de lista desplegable. Si **examinar** está disponible, selecciónelo y, a continuación, seleccione uno o más valores.

Para una propiedad con varios valores, el **heredar de primario o valores pred.** opción está disponible cuando se elige la flecha de lista desplegable en la columna a la derecha del nombre de la propiedad y, a continuación, elija **editar**. La opción se encuentra activada de forma predeterminada.

Observe que una página de propiedades solo muestra la configuración en el nivel actual de una propiedad con varios valores que hereda de otro nivel. Por ejemplo, si se selecciona un archivo en **el Explorador de soluciones** y seleccione C/C ++ **definiciones de preprocesador** propiedad, se muestran las definiciones de nivel de archivo, pero heredan las definiciones de nivel de proyecto no se muestran. Para ver los valores de nivel actual y heredados, elija la flecha de lista desplegable en la columna a la derecha del nombre de la propiedad y, a continuación, elija **editar**. Si usas el [modelo de proyecto de Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), este comportamiento también está en vigor para los objetos en los proyectos y archivos. Es decir, al consultar los valores de una propiedad en el nivel de archivo, no obtendrá los valores de esa misma propiedad en el nivel de proyecto. Tiene que obtener explícitamente los valores de la propiedad en el nivel de proyecto. Además, algunos valores heredados de una propiedad pueden proceder de una hoja de estilos, a la que no se tiene acceso mediante programación.

## <a name="in-this-section"></a>En esta sección

[Avanzadas, herramienta manifiesto, propiedades de configuración, \<NombreDeProyecto > página de propiedades de cuadro de diálogo](../ide/advanced-manifest-tool.md)

[Páginas de propiedades Línea de comandos](../ide/command-line-property-pages.md)

[Paso de compilación personalizada (Página de propiedades): General](../ide/custom-build-step-property-page-general.md)

[Agregar referencias](../ide/adding-references-in-visual-cpp-projects.md)

[Página de propiedades General (Archivo)](../ide/general-property-page-file.md)

[Página de propiedades General (Proyecto)](../ide/general-property-page-project.md)

[General, herramienta manifiesto, propiedades de configuración, \<NombreDeProyecto > página de propiedades de cuadro de diálogo](../ide/general-manifest-tool-configuration-properties.md)

[Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)

[Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)

[Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)

[Páginas de propiedades HLSL: Archivos de salida](../ide/hlsl-property-pages-output-files.md)

[Entrada y salida, herramienta, propiedades de configuración, manifiesto \<NombreDeProyecto > página de propiedades de cuadro de diálogo](../ide/input-and-output-manifest-tool.md)

[Aislamiento de COM, herramienta manifiesto, propiedades de configuración, \<NombreDeProyecto > página de propiedades de cuadro de diálogo](../ide/isolated-com-manifest-tool.md)

[Páginas de propiedades Vinculador](../ide/linker-property-pages.md)

[Página de propiedades Recursos administrados](../ide/managed-resources-property-page.md)

[Páginas de propiedades de la herramienta Manifiesto](../ide/manifest-tool-property-pages.md)

[Páginas de propiedades MIDL](../ide/midl-property-pages.md)

[Páginas de propiedades MIDL: Avanzadas](../ide/midl-property-pages-advanced.md)

[Páginas de propiedades MIDL: General](../ide/midl-property-pages-general.md)

[Páginas de propiedades MIDL: Resultados](../ide/midl-property-pages-output.md)

[Página de propiedades NMake](../ide/nmake-property-page.md)

[Páginas de propiedades Recursos](../ide/resources-property-pages.md)

[Directorios de VC++ (Página de propiedades)](../ide/vcpp-directories-property-page.md)

[Página de propiedades Referencias Web](../ide/web-references-property-page.md)

[Herramienta Generador de datos XML (Página de propiedades)](../ide/xml-data-generator-tool-property-page.md)

[Herramienta Generador de documentos XML (Páginas de propiedades)](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Vea también

[Cómo: Crear y quitar dependencias del proyecto](/visualstudio/ide/how-to-create-and-remove-project-dependencies)  
[Cómo: Crear y editar configuraciones](/visualstudio/ide/how-to-create-and-edit-configurations)  
