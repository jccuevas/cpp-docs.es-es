---
title: Procedimiento para usar eventos de compilación en proyectos de MSBuild
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060068"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Procedimiento para usar eventos de compilación en proyectos de MSBuild

Un evento de compilación es un comando que MSBuild ejecuta en una fase determinada del proceso de compilación. Los eventos *anteriores a la compilación* se producen antes de que comience la compilación; los eventos *anteriores a la vinculación* se producen antes de que comience el paso de vinculación; y los eventos *posteriores a la compilación* se producen una vez que la compilación ha finalizado correctamente. Los eventos de compilación solo se producen si tiene lugar el paso de compilación asociado. Por ejemplo, no se producirá un evento anterior a la vinculación si el paso de vinculación no se ejecuta.

Cada uno de los tres eventos de compilación se representa en un grupo de definiciones de elementos mediante un elemento de comando (`<Command>`) que se ejecuta y un elemento de mensaje (`<Message>`) que se muestra cuando **MSBuild** realiza el evento de compilación. Cada elemento es opcional y, si se especifica el mismo elemento varias veces, tiene prioridad la última aparición.

Se puede especificar un elemento opcional *de uso en la compilación* (`<`*build-event*`UseInBuild>`) en un grupo de propiedades para indicar si se ejecuta el evento de compilación. El valor del contenido de un elemento *de uso en la compilación* es **true** o **false**. De forma predeterminada, el evento de compilación se ejecuta a menos que su correspondiente elemento *de uso en la compilación* esté establecido en `false`.

La tabla siguiente contiene una lista con todos los elementos XML de eventos de compilación:

|Elemento XML|Descripción|
|-----------------|-----------------|
|`PreBuildEvent`|Este evento se ejecuta antes de que comience la compilación.|
|`PreLinkEvent`|Este evento se ejecuta antes de que comience el paso de vinculación.|
|`PostBuildEvent`|Este evento se ejecuta después de que finalice la compilación.|

En la tabla siguiente se muestra cada elemento *de uso en la compilación*:

|Elemento XML|Descripción|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Especifica si se va a ejecutar el evento *anterior a la compilación*.|
|`PreLinkEventUseInBuild`|Especifica si se va a ejecutar el evento *anterior a la vinculación*.|
|`PostBuildEventUseInBuild`|Especifica si se va a ejecutar el evento *posterior a la compilación*.|

## <a name="example"></a>Ejemplo

El ejemplo siguiente se puede agregar en el elemento Project del archivo myproject.vcxproj creado en [Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Un evento *anterior a la compilación* realiza una copia de main.cpp; un evento *anterior a la vinculación* realiza una copia de main.obj; y un evento *posterior a la compilación* realiza una copia de myproject.exe. Si el proyecto se compila con una configuración de versión, los eventos de compilación se ejecutan. Si el proyecto se compila con una configuración de depuración, los eventos de compilación no se ejecutan.

``` xml
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

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
[Tutorial: Uso de MSBuild para crear un proyecto de C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
