---
title: "C&#243;mo: Usar eventos de compilaci&#243;n en proyectos de MSBuild | Microsoft Docs"
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
  - "msbuild.cpp.howto.usebuildevents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), cómo: usar eventos de compilación en proyectos"
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo: Usar eventos de compilaci&#243;n en proyectos de MSBuild
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un evento de compilación es un comando que [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] ejecuta en una fase concreta del proceso de compilación.  El evento *de la pre\- compilación* se produce antes de que comience la compilación, el evento *de pre\- vínculo* aparece antes de que comience el paso de vinculación; y *el evento posterior a la* compilación se produce después de que finalice la compilación correctamente.  Un evento de compilación sólo aparece si el paso asociado de compilación aparece.  Por ejemplo, el evento anterior a la vinculación no se produce si no se ejecuta el paso de vinculación.  
  
 Cada uno de los tres eventos de compilación se representa en un grupo de definición de elementos mediante un elemento de comando \(`<Command>`\) que se ejecuta y un elemento de mensaje \(`<Message>`\) que se muestra cuando **MSBuild** ejecuta el evento de compilación.  Cada elemento es opcional y, si se especifica el mismo elemento varias veces, la última tiene prioridad.  
  
 El elemento opcional *de la uso\-en\- compilación* \(`<`*build\-event***UseInBuild**`>`\) se puede especificar en un grupo de propiedades para indicar si se ejecuta el evento de compilación.  El valor del contenido de un elemento *use\-in\-build* es `true` o `false`.  De forma predeterminada, un evento de compilación se ejecuta a menos que su elemento *use\-in\-build* esté establecido en `false`.  
  
 En la siguiente tabla se incluye cada elemento XML del evento de compilación:  
  
|Elemento XML|Descripción|  
|------------------|-----------------|  
|`PreBuildEvent`|Este evento se ejecuta antes de que comience la compilación.|  
|`PreLinkEvent`|Este evento se ejecuta antes de que comience el paso de vinculación.|  
|`PostBuildEvent`|Este evento se ejecuta cuando finaliza la compilación.|  
  
 En la siguiente tabla se incluye cada elemento *use\-in\-build*:  
  
|Elemento XML|Descripción|  
|------------------|-----------------|  
|`PreBuildEventUseInBuild`|Especifica si se debe ejecutar el evento *anterior a la compilación*.|  
|`PreLinkEventUseInBuild`|Especifica si se debe ejecutar el evento *anterior a la vinculación*.|  
|`PostBuildEventUseInBuild`|Especifica si se debe ejecutar el evento *posterior a la compilación*.|  
  
## Ejemplo  
 El siguiente ejemplo se puede agregar dentro del elemento Project del archivo myproject.vcxproj creado en [Tutorial: Usar MSBuild para crear un proyecto de Visual C\+\+](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).  Un evento *anterior a la compilación* realiza una copia de main.cpp, un evento *anterior a la vinculación* realiza una copia de main.obj y un evento *posterior a la compilación* realiza una copia de myproject.exe.  Si el proyecto se compila con una configuración de lanzamiento, se ejecutan los eventos de compilación.  Si el proyecto se compila con una configuración de depuración, no se ejecutan los eventos de compilación.  
  
```  
<ItemDefinitionGroup>  
  <PreBuildEvent>  
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>  
    <Message>Making a copy of main.cpp </Message>  
  </PreBuildEvent>  
  <PreLinkEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>  
    <Message>Making a copy of main.obj</Message>  
  </PreLinkEvent>  
  <PostBuildEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>  
    <Message>Making a copy of myproject.exe</Message>  
  </PostBuildEvent>  
</ItemDefinitionGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>  
</PropertyGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>  
</PropertyGroup>  
```  
  
## Vea también  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)   
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C\+\+](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)