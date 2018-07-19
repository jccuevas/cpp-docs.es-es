---
title: 'Cómo: agregar herramientas de compilación personalizadas a proyectos de MSBuild | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3793e4223d00f219cc4f1d7b09e67453901bd6d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368335"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Cómo: Agregar herramientas de compilación personalizadas a proyectos de MSBuild
Una herramienta de compilación personalizada es una herramienta de línea de comandos, definido por el usuario que está asociada a un archivo determinado.  
  
 Para un archivo determinado, especifique en el archivo de proyecto (.vcxproj) la línea de comandos para ejecutar, cualquier entrada adicional o archivos de salida y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida están actualizados con respecto a los archivos de entrada, se muestra el mensaje y se ejecuta la herramienta de línea de comandos.  
  
 Para especificar cuándo se ejecuta la herramienta de compilación personalizada, use uno o ambos de los `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` elementos XML en el archivo de proyecto. Por ejemplo, podría especificar que la herramienta de compilación personalizada ejecutar después el compilador MIDL y antes del compilador de C o C++. Especifique el `CustomBuildBeforeTargets` elemento que se va a ejecutar la herramienta antes de que se ejecute un destino determinado; el `CustomBuildAfterTargets` elemento que se va a ejecutar la herramienta después de un destino determinado; o ambos elementos para ejecutar la herramienta entre la ejecución de dos destinos. Si no se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es anterior a la **MIDL** destino.  
  
 Pasos de compilación personalizada y herramientas de compilación personalizadas comparten la información especificada en el `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` elementos XML. Especificar los destinos una vez en el archivo de proyecto.  
  
### <a name="to-add-a-custom-build-tool"></a>Para agregar una herramienta de compilación personalizada  
  
1.  Agregar un grupo de elementos al archivo de proyecto y agregar un elemento para cada archivo de entrada. Especifique el comando, las entradas adicionales, salidas y un mensaje como metadatos de elemento, como se muestra aquí. En este ejemplo se supone que existe un archivo "faq.txt" en el mismo directorio que el proyecto.  
  
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
  
1.  Agregue el siguiente grupo de propiedades al archivo de proyecto. Debe especificar al menos uno de los destinos, pero puede omitir el otro si solo está interesado en hacer que el paso de compilación se ejecute antes (o después de) un destino concreto. En este ejemplo se realiza el paso personalizado después de compilar pero antes de vincular.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Cómo: usar eventos de compilación de proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Procedimiento para agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)