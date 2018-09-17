---
title: 'Cómo: agregar un paso de compilación personalizado a proyectos de MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca8206024f4fbaf38b8161a9e12672782551db83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712184"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild

Un paso de compilación personalizado es un paso definido por el usuario en una compilación. Un paso de compilación personalizada se comporta como cualquier otro *herramienta de comando* paso, por ejemplo, el paso de la herramienta de compilación o vínculo estándar.

Especifique un paso de compilación personalizada en el archivo de proyecto (.vcxproj). El paso puede especificar una línea de comandos para ejecutar cualquier entrada adicional o archivos de salida y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida están actualizados con respecto a los archivos de entrada, se muestra el mensaje y se ejecuta el comando.

Para especificar la ubicación de la compilación personalizada paso en la secuencia de destinos de compilación, use uno o ambos de los `CustomBuildAfterTargets` y `CustomBuildBeforeTargets` los elementos XML en el archivo de proyecto. Por ejemplo, podría especificar que el paso de compilación personalizada se ejecuta después del destino de la herramienta de vínculo y antes del destino de la herramienta de manifiesto. El conjunto real de destinos disponibles depende de la compilación determinada.

Especifique el `CustomBuildBeforeTargets` elemento que se va a ejecutar el paso de compilación personalizada antes de que se ejecuta un destino determinado, el `CustomBuildAfterTargets` elemento que se va a ejecutar el paso después de ejecuta un destino determinado, o ambos elementos que se va a ejecutar el paso entre dos destinos adyacentes. Si se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es después de la **vínculo** destino.

Pasos de compilación personalizada y herramientas de compilación personalizadas comparten la información especificada en el `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` elementos XML. Por lo tanto, especifique los destinos una sola vez en el archivo de proyecto.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Para definir lo que se ejecuta en el paso de compilación personalizada

1. Agregar un grupo de propiedades al archivo de proyecto. En este grupo de propiedades, especifique el comando, sus entradas y salidas y un mensaje, como se muestra en el ejemplo siguiente. Este ejemplo crea un archivo .cab desde el archivo main.cpp que creó en [Tutorial: usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Para definir dónde se ejecutará el paso de compilación personalizado en la compilación

1. Agregue el siguiente grupo de propiedades al archivo de proyecto. Puede especificar ambos destinos, o puede omitir uno si desea que el paso personalizado se ejecute antes o después de un destino determinado. En este ejemplo se indica a **MSBuild** para realizar el paso personalizado después del paso de compilación, pero antes del paso del vínculo.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Vea también

[Tutorial: Usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Procedimiento para usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)<br/>
[Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)