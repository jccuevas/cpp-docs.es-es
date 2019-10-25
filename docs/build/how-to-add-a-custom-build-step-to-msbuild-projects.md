---
title: 'Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444918"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild

Un paso de compilación personalizada es un paso definido por el usuario en una compilación. Un paso de compilación personalizada se comporta como cualquier otro paso de la *herramienta de comandos* , como el paso estándar de compilación o de la herramienta de vinculación.

Especifique un paso de compilación personalizada en el archivo de proyecto (. vcxproj). El paso puede especificar la línea de comandos que se va a ejecutar, los archivos de entrada o salida adicionales y el mensaje que se va a mostrar. Si **msbuild** determina que los archivos de salida no están actualizados con respecto a los archivos de entrada, muestra el mensaje y ejecuta el comando.

Para especificar la ubicación del paso de compilación personalizada en la secuencia de destinos de compilación, use uno o los dos elementos XML `CustomBuildAfterTargets` y `CustomBuildBeforeTargets` en el archivo de proyecto. Por ejemplo, puede especificar que el paso de compilación personalizada se ejecute después del destino de la herramienta de vínculo y antes del destino de la herramienta de manifiesto. El conjunto real de destinos disponibles depende de la compilación concreta.

Especifique el elemento `CustomBuildBeforeTargets` para ejecutar el paso de compilación personalizada antes de que se ejecute un destino determinado, el elemento `CustomBuildAfterTargets` para ejecutar el paso después de que se ejecute un destino determinado o ambos elementos para ejecutar el paso entre dos destinos adyacentes. Si no se especifica ningún elemento, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es después del destino de **vínculo** .

Los pasos de compilación personalizada y las herramientas de compilación personalizadas comparten la información especificada en los elementos XML `CustomBuildBeforeTargets` y `CustomBuildAfterTargets`. Por consiguiente, especifique los destinos solo una vez en el archivo del proyecto.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Para definir lo que se ejecuta en el paso de compilación personalizada

1. Agregue un grupo de propiedades al archivo de proyecto. En este grupo de propiedades, especifique el comando, sus entradas y salidas, y un mensaje, como se muestra en el ejemplo siguiente. En este ejemplo se crea un archivo. cab a partir del archivo. cpp principal que creó en [Tutorial: usar MSBuild C++ para crear un proyecto](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Para definir dónde se ejecutará el paso de compilación personalizada en la compilación

1. Agregue el siguiente grupo de propiedades al archivo de proyecto. Puede especificar ambos destinos o puede omitir uno si solo desea que el paso personalizado se ejecute antes o después de un destino determinado. En este ejemplo se indica a **msbuild** que realice el paso personalizado después del paso de compilación, pero antes del paso de vínculo.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Vea también

[Tutorial: usar MSBuild para crear un C++ proyecto](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Procedimiento para usar eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
