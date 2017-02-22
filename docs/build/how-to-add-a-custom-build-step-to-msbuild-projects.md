---
title: "C&#243;mo: Agregar un paso de compilaci&#243;n personalizado a proyectos de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.addcustombuildstep"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), cómo: agregar un paso de compilación personalizado"
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Agregar un paso de compilaci&#243;n personalizado a proyectos de MSBuild
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un paso de compilación personalizado es un paso definido por el usuario en una compilación.  Un paso de compilación personalizado se comporta como cualquier otro paso de *herramienta de comando*, como el paso de la herramienta de compilación o vinculación estándar.  
  
 Especifique un paso de compilación personalizado en el archivo de proyecto \(.vcxproj\).  El paso puede especificar una línea de comandos que se debe ejecutar, cualquier archivo de entrada o salida adicional, y el mensaje que se debe mostrar.  Si **MSBuild** determina que los archivos de salida están anticuados con respecto a los archivos de entrada, muestra el mensaje y ejecuta el comando.  
  
 Para especificar la ubicación del paso de compilación personalizado en la secuencia de destinos de compilación, use uno de los elementos XML `CustomBuildBeforeTargets` y `CustomBuildAfterTargets`, o los dos, en el archivo de proyecto.  Por ejemplo, puede especificar que el paso de compilación personalizado se ejecute después del destino de la herramienta de vinculación y antes del destino de la herramienta de manifiesto.  El conjunto real de destinos disponibles depende de cada compilación.  
  
 Especifique el elemento `CustomBuildBeforeTargets` para ejecutar el paso de compilación personalizado antes de que se ejecute un destino determinado, el elemento `CustomBuildAfterTargets` para ejecutar el paso después de que se ejecute un destino determinado, o ambos elementos para ejecutar el paso entre dos destinos adyacentes.  Si no se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es después del destino **Link**.  
  
 Los pasos de compilación personalizados y las herramientas de compilación personalizadas comparten la información especificada en los elementos XML `CustomBuildAfterTargets` y `CustomBuildBeforeTargets`.  Por consiguiente, especifique esos destinos una sola vez en el archivo de proyecto.  
  
### Para definir qué ejecuta el paso de compilación personalizado  
  
1.  Agregue un grupo de propiedades al archivo de proyecto:  En este grupo de propiedades, especifique el comando, sus entradas y salidas, y un mensaje, tal como se muestra en el siguiente ejemplo.  En este ejemplo se crea un archivo .cab a partir del archivo main.cpp que se creó en [Tutorial: Usar MSBuild para crear un proyecto de Visual C\+\+](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### Para definir dónde se ejecutará el paso de compilación personalizado en la compilación  
  
1.  Agregue el siguiente grupo de propiedades al archivo de proyecto:  Puede especificar ambos destinos o puede omitir uno si desea que el paso personalizado se ejecute antes o después de un destino determinado.  En este ejemplo se indica a **MSBuild** que realice el paso personalizado después del paso de compilación pero antes del paso de vinculación.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## Vea también  
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C\+\+](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Cómo: Usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Cómo: Agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)