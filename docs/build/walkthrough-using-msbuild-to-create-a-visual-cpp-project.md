---
title: 'Tutorial: Uso de MSBuild para crear un proyecto de Visual C++'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422719"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Tutorial: Uso de MSBuild para crear un proyecto de Visual C++

En este tutorial se muestra cómo usar MSBuild para compilar un proyecto de Visual Studio C++ en un símbolo del sistema. Aprenderá a crear archivos de código fuente de C++ y un archivo de proyecto basado en XML para una aplicación de consola de Visual C++. Después de compilar el proyecto, aprenderá a personalizar el proceso de compilación.

En este tutorial se muestran las tareas siguientes:

- Crear archivos de código fuente de C++ para el proyecto.

- Crear el archivo de proyecto de MSBuild en XML.

- Usar MSBuild para compilar el proyecto.

- Usar MSBuild para personalizar el proyecto.

## <a name="prerequisites"></a>Requisitos previos

Necesitas lo siguiente para poder llevar a cabo este tutorial:

- Una copia de Visual Studio que tenga instalada la carga de trabajo **Desarrollo de escritorio con C++** .

- Conocimientos generales sobre el sistema MSBuild.

> [!NOTE]
> No siga este enfoque si va a editar el archivo de proyecto más adelante mediante el IDE de Visual Studio. Si crea un archivo .vcxproj manualmente, es posible que el IDE de Visual Studio no se pueda editar o cargar, sobre todo si el proyecto usa caracteres comodín en los elementos de proyecto.

> [!NOTE]
> La mayoría de las instrucciones de compilación de bajo nivel se encuentran en los archivos **.targets** y **.props** que se definen en el directorio VCTargets, almacenado en la propiedad `$(VCTargetsPath)`. La ruta de acceso predeterminada de estos archivos en Visual Studio 2019 Enterprise Edition es C:\Archivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props.

## <a name="creating-the-c-source-files"></a>Crear los archivos de origen de C++

En este tutorial, creará un proyecto que tiene un archivo de origen y un archivo de encabezado. El archivo de origen main.cpp contiene la función principal para la aplicación de consola. El archivo de encabezado main.h contiene código para incluir el archivo de encabezado iostream. Puede crear estos archivos de C++ mediante Visual Studio o un editor de texto, Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Para crear archivos de código fuente de C++ para el proyecto

1. Cree un directorio para el proyecto.

1. Cree un archivo con el nombre main.cpp y agregue el siguiente código a este archivo:

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

1. Cree un archivo con el nombre main.h y agregue el siguiente código a este archivo:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Crear el archivo de proyecto de MSBuild en XML

Un archivo de proyecto de MSBuild es un archivo XML que contiene un elemento raíz de proyecto (`<Project>`). En el proyecto de ejemplo siguiente, el elemento `<Project>` contiene siete elementos secundarios:

- Tres etiquetas de grupo de elementos (`<ItemGroup>`) que especifican la configuración del proyecto y la plataforma, el nombre del archivo de código fuente y el nombre del archivo de encabezado.

- Tres etiquetas de importación (`<Import>`) que especifican la ubicación de la configuración de Microsoft Visual C++.

- Una etiqueta de grupo de propiedades (`<PropertyGroup>`) que especifica la configuración del proyecto.

### <a name="to-create-the-msbuild-project-file"></a>Para crear el archivo de proyecto de MSBuild

1. Use un editor de texto para crear un archivo de proyecto con el nombre `myproject.vcxproj` y, después, agregue el siguiente elemento `<Project>` raíz. Inserte los elementos de los siguientes pasos del procedimiento entre las etiquetas `<Project>` raíz. (Use ToolsVersion="15.0 si usa Visual Studio 2017 o ToolsVersion="16.0" si usa Visual Studio 2019).

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Agregue estos dos elementos secundarios `<ProjectConfiguration>` en un elemento `<ItemGroup>`. El elemento secundario especifica las configuraciones de depuración y de versión de un sistema operativo Windows de 32 bits:

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

1. Agregue el siguiente elemento `<Import>` que especifica la ruta de acceso de la configuración predeterminada de C++ para este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Agregue el siguiente elemento de grupo de propiedades (`<PropertyGroup>`) que especifica dos propiedades del proyecto. (Use v141 si usa Visual Studio 2017 o v142 si usa Visual Studio 2019).

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Agregue el siguiente elemento `<Import>` que especifica la ruta de acceso de la configuración actual de C++ para este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Agregue el siguiente elemento secundario `<ClCompile>` en un elemento `<ItemGroup>`. El elemento secundario especifica el nombre del archivo de código fuente de C/C++ que se va a compilar:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` es un *destino de compilación* y se define en el directorio **VCTargets**.

1. Agregue el siguiente elemento secundario `<ClInclude>` en un elemento `<ItemGroup>`. El elemento secundario especifica el nombre del archivo de encabezado para el archivo de código fuente de C/C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Agregue el siguiente elemento `<Import>` que especifica la ruta de acceso del archivo que define el destino para este proyecto:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Completar el archivo de proyecto

El código de abajo muestra el archivo de proyecto completo que creó en el procedimiento anterior. (Use ToolsVersion="15.0" para Visual Studio 2017).

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

## <a name="using-msbuild-to-build-your-project"></a>Usar MSBuild para compilar el proyecto

Escriba este comando en el símbolo del sistema para compilar la aplicación de consola:

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild crea un directorio para los archivos de salida y, después, compila y vincula el proyecto para generar el programa Myproject.exe. Al finalizar el proceso de compilación, use este comando para ejecutar la aplicación desde la carpeta de depuración:

`myproject`

La aplicación debe mostrar "Hello, from MSBuild!" (Hola de parte de MSBuild) en la ventana de la consola.

## <a name="customizing-your-project"></a>Personalizar el proyecto

MSBuild permite ejecutar destinos de compilación predefinidos, aplicar propiedades definidas por el usuario y usar herramientas, eventos y pasos de compilación personalizados. En esta sección se explican las tareas siguientes:

- Usar MSBuild con destinos de compilación.

- Usar MSBuild con propiedades de compilación.

- Usar MSBuild con las herramientas y el compilador de 64 bits.

- Usar MSBuild con conjuntos de herramientas diferentes.

- Agregar personalizaciones de MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Usar MSBuild con destinos de compilación

Un *destino de compilación* es un conjunto con nombre de comandos predefinidos o definidos por el usuario que se pueden ejecutar durante la compilación. Use la opción de línea de comandos de destino (`/t`) para especificar un destino de compilación. Para el proyecto de ejemplo `myproject`, el destino **clean** predefinido elimina todos los archivos en la carpeta de depuración y crea un nuevo archivo de registro.

En el símbolo del sistema, escriba este comando para limpiar `myproject`:

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Usar MSBuild con propiedades de compilación

La opción de línea de comandos de propiedad (`/p`) permite reemplazar una propiedad en el archivo de compilación del proyecto. En el proyecto de ejemplo `myproject`, la configuración de compilación de versión o de depuración se especifica mediante la propiedad `Configuration`. El sistema operativo que está diseñado para ejecutar la aplicación compilada se especifica mediante la propiedad `Platform`.

En el símbolo del sistema, escriba este comando para crear una compilación de depuración de la aplicación `myproject` que está diseñada para ejecutarse en Windows de 32 bits.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Supongamos que el proyecto de ejemplo `myproject` también define una configuración para Windows de 64 bits y otra configuración para un sistema operativo personalizado denominado `myplatform`.

En el símbolo del sistema, escriba este comando para crear una versión de compilación que se ejecute en Windows de 64 bits.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

En el símbolo del sistema, escriba este comando para crear una versión de compilación para `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Usar MSBuild con las herramientas y el compilador de 64 bits

Si ha instalado Visual Studio en Windows de 64 bits, de forma predeterminada se instalan las herramientas cruzadas y nativas x64 de 64 bits. Puede configurar MSBuild para usar las herramientas y el compilador de 64 bits para compilar la aplicación mediante la configuración de la propiedad `PreferredToolArchitecture`. Esta propiedad no afecta a las propiedades de la plataforma o la configuración del proyecto. De forma predeterminada, se usa la versión de 32 bits de las herramientas. Para especificar la versión de 64 bits del compilador y las herramientas, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después del elemento `Microsoft.Cpp.default.props` \<Import />:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

En el símbolo del sistema, escriba este comando para usar las herramientas de 64 bits para compilar la aplicación.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Usar MSBuild con conjuntos de herramientas diferentes

Si tiene instalados conjuntos de herramientas y bibliotecas para otras versiones de Visual C++, MSBuild puede compilar las aplicaciones para la versión de Visual C++ actual o para las demás versiones instaladas. Por ejemplo, si ha instalado Visual Studio 2012, para especificar el conjunto de herramientas de Visual C++ 11.0 para Windows XP, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después del elemento `Microsoft.Cpp.props`\<Import />:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Para volver a compilar el proyecto con el conjunto de herramientas de Visual C++ 11.0 para Windows XP, escriba estos comandos:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Agregar personalizaciones de MSBuild

MSBuild ofrece varias maneras de personalizar el proceso de compilación. En estos temas se explica cómo agregar pasos de compilación, herramientas y eventos personalizados a un proyecto de MSBuild:

- [Cómo: Agregar un paso personalizado de compilación a proyectos de MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Cómo: Agregar herramientas personalizadas de compilación a proyectos de MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Cómo: Usar de eventos de compilación en proyectos de MSBuild](how-to-use-build-events-in-msbuild-projects.md)
