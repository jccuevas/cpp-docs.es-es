---
title: Procedimiento Agregar herramientas de compilación personalizadas a proyectos de MSBuild
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 05f160e650c0dd717d7ce0f29259f866d751fdba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188904"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Procedimiento Agregar herramientas de compilación personalizadas a proyectos de MSBuild

Una herramienta de compilación personalizada es una herramienta de línea de comandos, definido por el usuario que está asociada a un archivo determinado.

Para un archivo determinado, especifique en el archivo de proyecto (.vcxproj) en la línea de comandos para ejecutar, cualquier entrada adicional o los archivos de salida y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida están actualizados con respecto a los archivos de entrada, se muestra el mensaje y se ejecuta la herramienta de línea de comandos.

Para especificar cuándo se ejecuta la herramienta de compilación personalizada, use uno o ambos de los `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` los elementos XML en el archivo de proyecto. Por ejemplo, podría especificar que la herramienta de compilación personalizada ejecutar después el compilador de MIDL y antes del compilador de C o C++. Especifique el `CustomBuildBeforeTargets` elemento que se va a ejecutar la herramienta antes de que se ejecuta un destino determinado; el `CustomBuildAfterTargets` elemento que se va a ejecutar la herramienta después de un destino determinado; o ambos elementos para ejecutar la herramienta entre la ejecución de los dos destinos. Si se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es antes de la **MIDL** destino.

Pasos de compilación personalizada y herramientas de compilación personalizadas comparten la información especificada en el `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` elementos XML. Especificar los destinos de una vez en el archivo de proyecto.

### <a name="to-add-a-custom-build-tool"></a>Para agregar una herramienta de compilación personalizada

1. Agregue un grupo de elementos al archivo de proyecto y agregue un elemento para cada archivo de entrada. Especifique el comando, las entradas adicionales, salidas y un mensaje como metadatos de elementos, como se muestra aquí. En este ejemplo se supone que existe un archivo de "faq.txt" en el mismo directorio que el proyecto.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Para definir dónde se ejecutarán las herramientas de compilación personalizado en la compilación

1. Agregue el siguiente grupo de propiedades al archivo de proyecto. Debe especificar al menos uno de los destinos, pero puede omitir el otro si solo está interesado en hacer que el paso de compilación se ejecute antes (o después de) un destino determinado. Este ejemplo realiza el paso personalizado después de compilar, pero antes de vincular.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Vea también

[Tutorial: Uso de MSBuild para crear un proyecto de Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
