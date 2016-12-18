---
title: "C&#243;mo: Agregar herramientas de compilaci&#243;n personalizadas a proyectos de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.addcustombuildtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), cómo: agregar herramientas de compilación personalizadas"
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Agregar herramientas de compilaci&#243;n personalizadas a proyectos de MSBuild
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una herramienta de compilación personalizada es una herramienta de línea de comandos definida por el usuario que está asociada a un archivo determinado.  
  
 Para un archivo determinado, especifique en el archivo de proyecto \(.vcxproj\) la línea de comandos que se debe ejecutar, cualquier archivo de entrada o salida adicional, y el mensaje que se va a mostrar.  Si **MSBuild** determina que los archivos de salida están anticuados con respecto a los archivos de entrada, muestra el mensaje y ejecuta la herramienta de línea de comandos.  
  
 Para especificar cuándo se ejecuta la herramienta de compilación personalizada, use uno de los elementos XML `CustomBuildAfterTargets` y `CustomBuildBeforeTargets`, o ambos, en el archivo de proyecto.  Por ejemplo, podría especificar que la herramienta de compilación personalizada se ejecutase después del compilador de MIDL y antes del compilador de C\/C\+\+.  Especifique el elemento `CustomBuildBeforeTargets` para ejecutar la herramienta antes de que se ejecute un destino determinado; el elemento `CustomBuildAfterTargets` para ejecutar la herramienta después de un destino determinado; o ambos elementos para que la herramienta se ejecute entre la ejecución de los dos destinos.  Si no se especifica ninguno de los elementos, la herramienta de compilación personalizada se ejecuta en su ubicación predeterminada, que es antes del destino **MIDL**.  
  
 Los pasos de compilación personalizados y las herramientas de compilación personalizadas comparten la información especificada en los elementos XML `CustomBuildAfterTargets` y `CustomBuildBeforeTargets`.  Especifique los destinos una vez en el archivo de proyecto.  
  
### Para agregar una herramienta de compilación personalizada  
  
1.  Agregue un grupo de elementos al archivo de proyecto y agregue un elemento para cada archivo de entrada.  Especifique el comando, las entradas y salidas adicionales, y un mensaje como metadatos de elemento, tal como se muestra aquí.  En este ejemplo se supone que hay un archivo "faq.txt" en el mismo directorio que el proyecto.  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### Para definir dónde se ejecutarán las herramientas de compilación personalizadas en la compilación  
  
1.  Agregue el siguiente grupo de propiedades al archivo de proyecto:  Tiene que especificar al menos uno de los destinos, pero puede omitir el otro si solo le interesa que el paso de compilación se ejecute antes \(o después\) de un destino determinado.  En este ejemplo se ejecuta el paso personalizado después de la compilación pero antes de la vinculación.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## Vea también  
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C\+\+](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Cómo: Usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)