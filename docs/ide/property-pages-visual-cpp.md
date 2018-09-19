---
title: Páginas de propiedades (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.NotAProp.Edit
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1dc831dff6d1e3dbef4fc762712e8125a5b20e1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339714"
---
# <a name="property-pages-visual-c"></a>Páginas de propiedades (Visual C++)

Con las páginas de propiedades, puede especificar la configuración de los proyectos de Visual Studio. Para abrir el cuadro de diálogo **Páginas de propiedades** de un proyecto de Visual Studio, en el menú **Proyecto**, haga clic en **Propiedades**.

Puede especificar la configuración del proyecto para que se aplique a todas las configuraciones de compilación o bien puede especificar propiedades de proyecto diferentes para cada configuración de compilación. Por ejemplo, puede especificar ciertos valores para la configuración de versión y otros para la configuración de depuración.

No todas las páginas disponibles se muestran necesariamente en el cuadro de diálogo **Páginas de propiedades**. Las páginas que se muestran dependen de los tipos de archivo del proyecto.

Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

Para proyectos distintos de Windows, vea [Referencia de las páginas de propiedades de un proyecto de Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Propiedades predeterminadas frente a propiedades modificadas

Cuando se usa el cuadro de diálogo **Nuevo proyecto** para crear un proyecto, Visual Studio usa la plantilla de proyecto especificada para inicializar las propiedades del proyecto. Por lo tanto, los valores de las propiedades de la plantilla pueden considerarse como valores predeterminados para ese tipo de proyecto. En otros tipos de proyecto, las propiedades pueden tener diferentes valores predeterminados.

Un valor de propiedad de proyecto aparece en negrita si se ha modificado. Una propiedad de proyecto puede modificarse por las razones siguientes:

- El Asistente para aplicaciones cambia la propiedad porque necesita un valor de propiedad diferente al que se ha especificado en la plantilla de proyecto.

- En el cuadro de diálogo **Nuevo proyecto** se especifica otro valor de propiedad.

- El usuario especifica un valor de propiedad distinto en una página de propiedades de proyecto.

> [!TIP]
> Para ver el conjunto final de valores de propiedad que MSBuild usa para compilar el proyecto, examine el archivo de salida del preprocesador, que se puede generar mediante esta línea de comandos: **MSBuild /preprocess:** *nombre_de_archivo_de_salida_del_preprocesador*<sub>opt</sub> *nombre_de_archivo_del_proyecto*<sub>opt</sub>.

## <a name="resetting-properties"></a>Restablecer propiedades

Cuando ve el cuadro de diálogo **Páginas de propiedades** de un proyecto y el nodo del proyecto está seleccionado en el **Explorador de soluciones**, para muchas propiedades, puede seleccionar **Heredar de primario o valores pred. del proyecto** o modificar el valor de otra manera.

Cuando ve el cuadro de diálogo **Páginas de propiedades** de un proyecto y un archivo está seleccionado en el **Explorador de soluciones**, para muchas propiedades, puede seleccionar **Heredar de primario o valores pred. del proyecto** o modificar el valor de otra manera. Sin embargo, si el proyecto contiene muchos archivos que tienen valores de propiedad que difieren de los valores predeterminados del proyecto, se tardará más tiempo en compilarlo.

> [!TIP]
> Para actualizar el cuadro de diálogo **Páginas de propiedades** de modo que muestre las selecciones más recientes, haga clic en **Aplicar**.

La mayoría de los valores predeterminados del proyecto son valores predeterminados del sistema (plataforma). Algunos valores predeterminados del proyecto derivan de las hojas de estilo que se aplican al actualizar las propiedades de la sección **Valores predeterminados del proyecto** de la página de propiedades de configuración **General** del proyecto. Para obtener más información, vea [Página de propiedades General (Proyecto)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Especificar valores definidos por el usuario

Debe definir el valor de algunas propiedades. Un valor definido por el usuario puede contener uno o más caracteres alfanuméricos o nombres de macro de archivo de proyecto. Algunas de estas propiedades pueden tomar un único valor definido por el usuario, pero otras pueden tomar una lista delimitada por puntos y coma de varios valores.

Para especificar un valor definido por el usuario para una propiedad, o una lista si la propiedad puede tomar varios valores definidos por el usuario, en la columna situada a la derecha del nombre de la propiedad, realice una de las siguientes acciones:

- Escriba el valor o la lista de valores.

- Haga clic en la flecha desplegable. Si **Editar** está disponible, haga clic en esa opción y, después, en el cuadro de texto, escriba el valor o la lista de valores. Un medio alternativo de especificar una lista es escribir cada valor en una línea independiente del cuadro de texto. En la página de propiedades, los valores se mostrarán como una lista delimitada por puntos y coma.

   Para insertar una macro de archivo de proyecto como un valor, haga clic en **Macros** y, después, haga doble clic en el nombre de la macro.

- Haga clic en la flecha desplegable. Si **Examinar** está disponible, haga clic en esa opción y, después, seleccione uno o más valores.

Para una propiedad con varios valores, la opción **Heredar de primario o valores pred. del proyecto** está disponible si hace clic en la flecha desplegable de la columna situada a la derecha del nombre de la propiedad y, después, hace clic en **Editar**. La opción se encuentra activada de forma predeterminada.

Observe que una página de propiedades solo muestra la configuración en el nivel actual de una propiedad con varios valores que hereda de otro nivel. Por ejemplo, si se selecciona un archivo en el **Explorador de soluciones** y la propiedad **Definiciones de preprocesador** de C/C ++, se muestran las definiciones de nivel de archivo pero no las definiciones de nivel de proyecto heredadas. Para ver los valores de nivel actual y los heredados, haga clic en la flecha desplegable de la columna situada a la derecha del nombre de la propiedad y, después, seleccione **Editar**. Si se usa el [modelo de proyecto de Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), este comportamiento también afecta a los objetos de los proyectos y archivos. Es decir, al consultar los valores de una propiedad en el nivel de archivo, no obtendrá los valores de esa misma propiedad en el nivel de proyecto. Tiene que obtener explícitamente los valores de la propiedad en el nivel de proyecto. Además, algunos valores heredados de una propiedad pueden proceder de una hoja de estilos, a la que no se tiene acceso mediante programación.

## <a name="in-this-section"></a>En esta sección

[Avanzadas, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<NombreDeProyecto> (Cuadro de diálogo)](../ide/advanced-manifest-tool.md)

[Páginas de propiedades Línea de comandos](../ide/command-line-property-pages.md)

[Paso de compilación personalizada (Página de propiedades): General](../ide/custom-build-step-property-page-general.md)

[Agregar referencias](../ide/adding-references-in-visual-cpp-projects.md)

[Página de propiedades General (Archivo)](../ide/general-property-page-file.md)

[Página de propiedades General (Proyecto)](../ide/general-property-page-project.md)

[General, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<NombreDeProyecto> (Cuadro de diálogo)](../ide/general-manifest-tool-configuration-properties.md)

[Páginas de propiedades HLSL](../ide/hlsl-property-pages.md)

[Páginas de propiedades HLSL: Avanzadas](../ide/hlsl-property-pages-advanced.md)

[Páginas de propiedades HLSL: General](../ide/hlsl-property-pages-general.md)

[Páginas de propiedades HLSL: Archivos de salida](../ide/hlsl-property-pages-output-files.md)

[Entrada y salida, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<NombreDeProyecto> (Cuadro de diálogo)](../ide/input-and-output-manifest-tool.md)

[COM aislado, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<NombreDeProyecto> (Cuadro de diálogo)](../ide/isolated-com-manifest-tool.md)

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
