---
title: 'Tutorial: Usar MSBuild para crear un proyecto de Visual C++'
ms.date: 05/06/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: 8fb985cbf4e471589946e730e8bb09b43f0a5d84
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446210"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Tutorial: Usar MSBuild para crear un proyecto de Visual C++

Este tutorial muestra cómo usar MSBuild para compilar un Visual Studio C++ proyecto en un símbolo del sistema. Obtendrá información sobre cómo crear los archivos de origen de C++ y un archivo de proyecto basado en XML para una aplicación de consola de Visual C++. Después de compilar el proyecto, obtendrá información sobre cómo personalizar el proceso de compilación.

En este tutorial se muestran las tareas siguientes:

- Crear los archivos de origen de C++ para el proyecto.

- Crear el archivo de proyecto XML de MSBuild.

- Uso de MSBuild para compilar el proyecto.

- Uso de MSBuild para personalizar el proyecto.

## <a name="prerequisites"></a>Requisitos previos

Necesitas lo siguiente para poder llevar a cabo este tutorial:

- Una copia de Visual Studio con el **desarrollo de escritorio con C++** carga de trabajo instalada.

- Conocimientos generales sobre el sistema MSBuild.

> [!NOTE]
> No utilice este enfoque si va a editar el archivo de proyecto más adelante mediante el IDE de Visual Studio. Si crea un archivo .vcxproj manualmente, el IDE de Visual Studio posible que no pueda editar o cargarla, especialmente si el proyecto utiliza caracteres comodín en los elementos de proyecto.

> [!NOTE]
> La mayoría de las instrucciones de compilación de bajo nivel se encuentran en el **.targets** y **.props** archivos que se definen en el directorio VCTargets, almacenado en la propiedad `$(VCTargetsPath)`. La ruta de acceso predeterminada de estos archivos en Visual Studio 2019 Enterprise Edition es C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props.

## <a name="creating-the-c-source-files"></a>Creación de los archivos de código fuente de C++

En este tutorial, creará un proyecto que tiene un archivo de origen y un archivo de encabezado. El archivo de origen main.cpp contiene la función principal para la aplicación de consola. El archivo de encabezado main.h contiene código para incluir el archivo de encabezado iostream. Puede crear estos archivos de C++ con Visual Studio o un texto editor como código de Visual Studio.

### <a name="to-create-the-c-source-files-for-your-project"></a>Para crear los archivos de origen de C++ para el proyecto

1. Cree un directorio para el proyecto.

1. Cree un archivo que se denomine main.cpp y agregue el código siguiente a este archivo:

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

1. Cree un archivo que se denomine main.h y agregue el código siguiente a este archivo:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Creación del archivo de proyecto de MSBuild XML

Un archivo de proyecto de MSBuild es un archivo XML que contiene un elemento raíz del proyecto (`<Project>`). En el proyecto de ejemplo siguiente, la `<Project>` elemento contiene siete elementos secundarios:

- Tres etiquetas de grupo de elementos (`<ItemGroup>`) que especifican la configuración del proyecto y plataforma, el nombre del archivo de origen y el nombre del archivo de encabezado.

- Tres etiquetas de importación (`<Import>`) que especifican la ubicación de configuración de Microsoft Visual C++.

- Una etiqueta de grupo de propiedades (`<PropertyGroup>`) que especifica la configuración del proyecto.

### <a name="to-create-the-msbuild-project-file"></a>Para crear el archivo de proyecto de MSBuild

1. Utilice un editor de texto para crear un archivo de proyecto que se denomina `myproject.vcxproj`y, a continuación, agregue la siguiente raíz `<Project>` elemento. Inserte los elementos de los siguientes pasos del procedimiento entre la raíz `<Project>` etiquetas. (Use ToolsVersion = "15.0" Si está utilizando Visual Studio 2017.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Agregue las dos siguientes `<ProjectConfiguration>` elementos secundarios en un `<ItemGroup>` elemento. El elemento secundario especifica la depuración y lanzamiento de las configuraciones para un sistema operativo de Windows de 32 bits:

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

1. Agregue las siguientes `<Import>` elemento que especifica la ruta de acceso de la configuración de C++ de forma predeterminada para este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Agregue el siguiente elemento de grupo de propiedades (`<PropertyGroup>`) que especifica dos propiedades del proyecto. (Utilice v141 si usa Visual Studio 2017).

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Agregue las siguientes `<Import>` elemento que especifica la ruta de acceso de la configuración actual de C++ para este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Agregue el siguiente `<ClCompile>` elemento secundario de un `<ItemGroup>` elemento. El elemento secundario especifica el nombre del archivo de código fuente de C o C++ para compilar:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` es un *destino de compilación* y se define en el **VCTargets** directory.

1. Agregue el siguiente `<ClInclude>` elemento secundario de un `<ItemGroup>` elemento. El elemento secundario especifica el nombre del archivo de encabezado para el archivo de código fuente de C o C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Agregue las siguientes `<Import>` elemento que especifica la ruta de acceso del archivo que define el destino de este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Archivo de proyecto completo

El código siguiente muestra el archivo de proyecto completo que creó en el procedimiento anterior. (Use ToolsVersion = "15.0" para Visual Studio 2017.)

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v142</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>Uso de MSBuild para compilar el proyecto

Escriba el siguiente comando en el símbolo del sistema para compilar la aplicación de consola:

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild crea un directorio para los archivos de salida y, a continuación, compila y vincula el proyecto para generar el programa Myproject.exe. Al finalizar el proceso de compilación, use el siguiente comando para ejecutar la aplicación desde la carpeta de depuración:

`myproject`

La aplicación debe mostrar "Hello, from MSBuild!" en la ventana de la consola.

## <a name="customizing-your-project"></a>Personalizar el proyecto

MSBuild permite ejecutar destinos de compilación predefinidos, aplicar propiedades definidas por el usuario y usar herramientas personalizadas, eventos y pasos de compilación. En esta sección muestra las tareas siguientes:

- Usar MSBuild con destinos de compilación.

- Usar MSBuild con propiedades de compilación.

- Usar MSBuild con el compilador de 64 bits y herramientas.

- Usar MSBuild con diferentes conjuntos de herramientas.

- Agregar personalizaciones de MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Usar MSBuild con destinos de compilación

Un *destino de compilación* es un conjunto de comandos predefinidos o definidos por el usuario que se pueden ejecutar durante la compilación. Utilice la opción de línea de comandos de destino (`/t`) para especificar un destino de compilación. Para el `myproject` proyecto de ejemplo, predefinido **limpia** elimina todos los archivos en la carpeta de depuración y crea un nuevo archivo de registro de destino.

En el símbolo del sistema, escriba el siguiente comando para limpiar `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Usar MSBuild con propiedades de compilación

La opción de línea de comandos property (`/p`) permite reemplazar una propiedad en el archivo de compilación del proyecto. En el `myproject` configuración de compilación de proyecto, el lanzamiento o depuración de ejemplo se especifica mediante el `Configuration` propiedad. Y el sistema operativo que está diseñado para ejecutar la aplicación compilada se especifica mediante el `Platform` propiedad.

En el símbolo del sistema, escriba el siguiente comando para crear una compilación de depuración de la `myproject` aplicación que está diseñada para ejecutarse en Windows de 32 bits.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Suponga que el `myproject` ejemplo proyecto también define una configuración para Windows de 64 bits y otra configuración para un sistema operativo personalizado denominado `myplatform`.

En el símbolo del sistema, escriba el siguiente comando para crear una versión de compilación que se ejecuta en Windows de 64 bits.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

En el símbolo del sistema, escriba el siguiente comando para crear una versión de lanzamiento para `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Usar MSBuild con el compilador de 64 bits y herramientas

Si ha instalado Visual Studio en Windows de 64 bits, de forma predeterminada, se instalan el x64 64 bits nativa y cruzada herramientas. Puede configurar MSBuild para usar el compilador de 64 bits y herramientas para compilar la aplicación estableciendo el `PreferredToolArchitecture` propiedad. Esta propiedad no afecta a las propiedades de configuración o la plataforma del proyecto. De forma predeterminada, se usa la versión de 32 bits de las herramientas. Para especificar la versión de 64 bits del compilador y herramientas, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después la `Microsoft.Cpp.default.props` \<Import / > elemento:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

En el símbolo del sistema, escriba el siguiente comando para usar las herramientas de 64 bits para compilar la aplicación.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Usar MSBuild con un conjunto de herramientas diferente

Si tiene los conjuntos de herramientas y bibliotecas para otras versiones de Visual C++ instalado, MSBuild puede compilar aplicaciones para la versión actual de Visual C++ o para las demás versiones instaladas. Por ejemplo, si ha instalado Visual Studio 2012, para especificar el conjunto de herramientas 11.0 de Visual C++ para Windows XP, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después la `Microsoft.Cpp.props` \<Import / > elemento:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Para volver a generar el proyecto con el conjunto de herramientas de Visual C++ 11.0 Windows XP, escriba los siguientes comandos:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Agregar personalizaciones de MSBuild

MSBuild proporciona varias maneras de personalizar el proceso de compilación. Los temas siguientes muestran cómo agregar pasos de compilación personalizados, herramientas y los eventos a su proyecto de MSBuild:

- [Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Cómo: Agregar herramientas personalizadas de compilación a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)
