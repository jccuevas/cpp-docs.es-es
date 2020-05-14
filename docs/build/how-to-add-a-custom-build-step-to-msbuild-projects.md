---
title: Procedimiento para agregar un paso personalizado de compilación a proyectos de MSBuild
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444918"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Procedimiento para agregar un paso personalizado de compilación a proyectos de MSBuild

Un paso de compilación personalizado es un paso definido por el usuario en una compilación. Un paso de compilación personalizado se comporta como cualquier otro paso de *herramienta de comando*, como el paso estándar de compilación o vinculación.

Especifique un paso de compilación personalizado en el archivo del proyecto (.vcxproj). El paso puede especificar una línea de comandos para su ejecución, cualquier archivo de entrada o salida adicional, y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida no están actualizados con respecto a los archivos de entrada, muestra el mensaje y ejecuta el comando.

Para especificar la ubicación del paso de compilación personalizado en la secuencia de destinos de compilación, use uno de los elementos XML `CustomBuildAfterTargets` y `CustomBuildBeforeTargets` (o los dos) del archivo del proyecto. Por ejemplo, puede especificar que el paso de compilación personalizado se ejecute después del destino de la herramienta de vínculo y antes del de la herramienta de manifiesto. El conjunto real de destinos disponibles depende de la compilación concreta.

Especifique el elemento `CustomBuildBeforeTargets` para ejecutar el paso de compilación personalizado antes de que se ejecute un destino determinado, el elemento `CustomBuildAfterTargets` para ejecutar el paso después de que se ejecute un destino determinado, o bien ambos elementos para ejecutar el paso entre dos destinos adyacentes. Si no se especifica ningún elemento, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es después del destino **Vínculo**.

Los pasos de compilación personalizados y las herramientas de compilación personalizadas comparten la información especificada en los elementos XML `CustomBuildBeforeTargets` y `CustomBuildAfterTargets`. Por tanto, especifique esos destinos solo una vez en el archivo del proyecto.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Para definir qué ejecuta el paso de compilación personalizado

1. Agregue un grupo de propiedades al archivo del proyecto. En este grupo de propiedades, especifique el comando, sus entradas y salidas, y un mensaje, como se muestra en el ejemplo siguiente. En este ejemplo se crea un archivo .cab a partir del archivo .cpp principal creado en [Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Para definir dónde se ejecutará el paso de compilación personalizado en la compilación

1. Agregue el grupo de propiedades siguiente al archivo del proyecto. Puede especificar ambos destinos o puede omitir uno si solo quiere que el paso personalizado se ejecute antes o después de un destino determinado. En este ejemplo se indica a **MSBuild** que ejecute el paso personalizado después del paso de compilación, pero antes del paso de vínculo.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Vea también

[Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Cómo: Agregar herramientas personalizadas de compilación a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
