---
title: "Cómo: agregar un paso de compilación personalizado a proyectos de MSBuild | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.addcustombuildstep
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d664b9fad6a9ec67dc009a90171119036dc13cde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild
Un paso de compilación personalizado es un paso definido por el usuario en una compilación. Un paso de compilación personalizada se comporta como cualquier otro *herramienta de comando* paso, por ejemplo, el paso de herramienta de compilación o vinculación estándar.  
  
 Especifique un paso de compilación personalizada en el archivo de proyecto (.vcxproj). El paso puede especificar una línea de comandos para su ejecución, cualquier entrada adicional o archivos de salida y un mensaje para mostrar. Si **MSBuild** determina que los archivos de salida están actualizados con respecto a los archivos de entrada, se muestra el mensaje y se ejecuta el comando.  
  
 Para especificar la ubicación de la compilación personalizada paso en la secuencia de destinos de compilación, use uno o ambos de los `CustomBuildAfterTargets` y `CustomBuildBeforeTargets` elementos XML en el archivo de proyecto. Por ejemplo, podría especificar que el paso de compilación personalizada se ejecuta después del destino de la herramienta de vínculo y antes que el destino de la herramienta de manifiesto. El conjunto real de destinos disponibles depende de cada compilación.  
  
 Especifique el `CustomBuildBeforeTargets` elemento que se va a ejecutar el paso de compilación personalizada antes de que se ejecute un destino determinado, el `CustomBuildAfterTargets` elemento que se va a ejecutar el paso cuando se ejecute un destino determinado, o ambos elementos que se va a ejecutar el paso entre dos destinos adyacentes. Si no se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es después de la **vínculo** destino.  
  
 Pasos de compilación personalizada y herramientas de compilación personalizadas comparten la información especificada en el `CustomBuildBeforeTargets` y `CustomBuildAfterTargets` elementos XML. Por lo tanto, especifique los destinos una sola vez en el archivo de proyecto.  
  
### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Para definir lo que se ejecuta en el paso de compilación personalizada  
  
1.  Agregar un grupo de propiedades al archivo de proyecto. En este grupo de propiedades, especifique el comando, sus entradas y salidas y un mensaje, como se muestra en el ejemplo siguiente. Este ejemplo crea un archivo .cab desde el archivo main.cpp que creó en [Tutorial: usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).  
  
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
  
1.  Agregue el siguiente grupo de propiedades al archivo de proyecto. Se pueden especificar ambos destinos o puede omitir uno si solo desea que el paso personalizado se ejecute antes o después de un destino determinado. Este ejemplo se indica a **MSBuild** para realizar el paso personalizado después del paso de compilación pero antes del paso de vínculo.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Cómo: usar eventos de compilación de proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)