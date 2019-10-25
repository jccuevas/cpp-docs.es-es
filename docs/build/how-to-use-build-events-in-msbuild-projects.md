---
title: Procedimiento Usar eventos de compilación en proyectos de MSBuild
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060068"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Procedimiento Usar eventos de compilación en proyectos de MSBuild

Un evento de compilación es un comando que MSBuild realiza en una fase determinada del proceso de compilación. El evento *anterior a la compilación* se produce antes de que se inicie la compilación; el evento *anterior a* la vinculación se produce antes de que se inicie el paso de vínculo; y el evento *posterior a la compilación* se produce una vez finalizada correctamente la compilación. Un evento de compilación solo se produce si se produce el paso de compilación asociado. Por ejemplo, el evento anterior a la vinculación no se produce si el paso de vínculo no se ejecuta.

Cada uno de los tres eventos de compilación se representa en un grupo de definiciones de elemento mediante`<Command>`un elemento Command () que se ejecuta y`<Message>`un elemento message () que se muestra cuando **msbuild** realiza el evento de compilación. Cada elemento es opcional y, si se especifica el mismo elemento varias veces, la última aparición tiene prioridad.

Se puede especificar un elemento *de uso en compilación* opcional (`<`*Build-Event*`UseInBuild>`) en un grupo de propiedades para indicar si se ejecuta el evento de compilación. El valor del contenido de un elemento de *uso en la compilación* es **true** o **false**. De forma predeterminada, se ejecuta un evento de compilación a menos que su elemento *de uso en compilación* correspondiente `false`se establezca en.

En la tabla siguiente se enumeran los elementos XML de los eventos de compilación:

|Elemento XML|DESCRIPCIÓN|
|-----------------|-----------------|
|`PreBuildEvent`|Este evento se ejecuta antes de que comience la compilación.|
|`PreLinkEvent`|Este evento se ejecuta antes de que comience el paso de vínculo.|
|`PostBuildEvent`|Este evento se ejecuta después de que finalice la compilación.|

En la tabla siguiente se enumeran todos los elementos *de uso en la compilación* :

|Elemento XML|DESCRIPCIÓN|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Especifica si se debe ejecutar el evento *anterior a la compilación* .|
|`PreLinkEventUseInBuild`|Especifica si se debe ejecutar el evento *anterior a* la vinculación.|
|`PostBuildEventUseInBuild`|Especifica si se debe ejecutar el evento *posterior a la compilación* .|

## <a name="example"></a>Ejemplo

El ejemplo siguiente se puede Agregar dentro del elemento Project del archivo de proyecto. vcxproj creado en [el tutorial: Usar MSBuild para crear un C++ proyecto](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Un evento *anterior a la compilación* realiza una copia de Main. cpp; un evento *anterior a la vinculación* realiza una copia de Main. obj; y un evento *posterior a la compilación* realiza una copia de mis proyectos. exe. Si el proyecto se compila con una configuración de versión, se ejecutan los eventos de compilación. Si el proyecto se compila mediante una configuración de depuración, los eventos de compilación no se ejecutan.

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
