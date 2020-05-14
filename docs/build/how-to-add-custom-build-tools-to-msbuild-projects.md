---
title: Procedimiento para agregar herramientas personalizadas de compilación a proyectos de MSBuild
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220717"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Procedimiento para agregar herramientas personalizadas de compilación a proyectos de MSBuild

Una herramienta de compilación personalizada es una herramienta de línea de comandos definida por el usuario que está asociada a un archivo determinado.

Para un archivo en concreto, especifique en el archivo de proyecto (.vcxproj) la línea de comandos que se va a ejecutar, cualquier archivo de entrada o salida adicional, y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida no están actualizados con respecto a los archivos de entrada, muestra el mensaje y ejecuta la herramienta de línea de comandos.

Para especificar el momento en el que se ejecuta la herramienta de compilación personalizada, use uno de los elementos XML `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` (o ambos) en el archivo de proyecto. Por ejemplo, puede especificar que la herramienta de compilación personalizada se ejecute después del compilador de MIDL y antes del compilador de C/C++. Especifique el elemento `CustomBuildBeforeTargets` para ejecutar la herramienta antes de que se ejecute un destino determinado, el elemento `CustomBuildAfterTargets` para ejecutar la herramienta después de un destino determinado, o bien ambos elementos para ejecutar la herramienta entre la ejecución de dos destinos. Si no se especifica ningún elemento, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es antes del destino **MIDL**.

Los pasos de compilación personalizados y las herramientas de compilación personalizadas comparten la información especificada en los elementos XML `CustomBuildBeforeTargets` y `CustomBuildAfterTargets`. Especifique esos destinos una vez en el archivo del proyecto.

### <a name="to-add-a-custom-build-tool"></a>Para agregar una herramienta de compilación personalizada

1. Agregue un grupo de elementos al archivo de proyecto y agregue un elemento para cada archivo de entrada. Especifique el comando, las entradas adicionales, las salidas y un mensaje como metadatos del elemento, como se muestra aquí. En este ejemplo se supone que existe un archivo "faq.txt" en el mismo directorio que el proyecto.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Para definir dónde se ejecutarán las herramientas de compilación personalizadas en la compilación

1. Agregue el grupo de propiedades siguiente al archivo del proyecto. Debe especificar al menos uno de los destinos, pero puede omitir el otro si solo le interesa que el paso de compilación se ejecute antes (o después) de un destino determinado. En este ejemplo se realiza el paso personalizado después de la compilación, pero antes de la vinculación.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Vea también

[Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
