---
title: "Cómo: usar eventos de compilación de proyectos de MSBuild | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msbuild.cpp.howto.usebuildevents
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc8b3b21cdc9aad183f39bf709f93e022e790eef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Cómo: Usar eventos de compilación en proyectos de MSBuild
Un evento de compilación es un comando que [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] lleva a cabo en una determinada fase del proceso de compilación. El *anterior a la compilación* evento tiene lugar antes de que comience la compilación; el *anterior a la vinculación* evento tiene lugar antes de iniciar el paso de vínculo; y la *posterior a la compilación* evento tiene lugar después de la compilación finaliza correctamente. Se produce un evento de compilación sólo si se produce el paso de compilación asociado. Por ejemplo, el evento anterior a la vinculación no se produce si no se ejecuta el paso de vinculación.  
  
 Cada uno de los eventos de tres compilación se representa en un grupo de definición de elemento mediante un elemento command (`<Command>`) que se ejecuta y un elemento de mensaje (`<Message>`) que es que se muestran cuando **MSBuild** realiza el evento de compilación. Cada elemento es opcional y, si especifica varias veces el mismo elemento, la última aparición tiene prioridad.  
  
 Opcional *use-in-build* elemento (`<`*eventos de compilación***UseInBuild**`>`) se pueden especificar en un grupo de propiedades para indicar si el se ejecuta el evento de compilación. El valor del contenido de un *use-in-build* elemento sea `true` o `false`. De manera predeterminada, un evento de compilación se ejecuta a menos que el correspondiente *use-in-build* elemento está establecido en `false`.  
  
 La tabla siguiente enumera cada elemento XML de eventos de compilación:  
  
|Elemento XML|Descripción|  
|-----------------|-----------------|  
|`PreBuildEvent`|Este evento se ejecuta antes de que comience la compilación.|  
|`PreLinkEvent`|Este evento se ejecuta antes de que comience el paso de vinculación.|  
|`PostBuildEvent`|Este evento se ejecuta una vez finalizada la compilación.|  
  
 En la tabla siguiente enumera cada *use-in-build* elemento:  
  
|Elemento XML|Descripción|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|Especifica si se debe ejecutar el *anterior a la compilación* eventos.|  
|`PreLinkEventUseInBuild`|Especifica si se debe ejecutar el *anterior a la vinculación* eventos.|  
|`PostBuildEventUseInBuild`|Especifica si se debe ejecutar el *posterior a la compilación* eventos.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se puede agregar dentro del elemento de proyecto del archivo myproject.vcxproj creado en [Tutorial: usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). A *anterior a la compilación* evento hace una copia de main.cpp; *anterior a la vinculación* evento hace una copia de main.obj; y un *posterior a la compilación* evento hace una copia de myproject.exe. Si se compila el proyecto con una configuración de lanzamiento, se ejecutan los eventos de compilación. Si se compila el proyecto con una configuración de depuración, no se ejecutan los eventos de compilación.  
  
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
  
## <a name="see-also"></a>Vea también  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)   
 [Tutorial: Usar MSBuild para crear un proyecto de Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)