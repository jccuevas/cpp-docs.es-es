---
title: "Tutorial: Usar MSBuild para crear un proyecto de Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.walkthrough.createproject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), tutorial: crear un proyecto"
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Usar MSBuild para crear un proyecto de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tutorial muestra cómo usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para compilar un proyecto de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en un símbolo del sistema.  Obtendrá información sobre cómo crear los archivos de origen de C\+\+ y un archivo de proyecto basado en XML para una aplicación de consola de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  Después de compilar el proyecto, aprenderá a personalizar el proceso de compilación.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear los archivos de origen de C\+\+ para el proyecto.  
  
-   Crear el archivo de proyecto XML de [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)].  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para compilar el proyecto.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para personalizar el proyecto.  
  
## Requisitos previos  
 Necesita lo siguiente para poder llevar a cabo este tutorial:  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   Conocimientos generales sobre el sistema de [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)].  
  
## Crear los archivos de origen de C\+\+  
 En este tutorial, creará un proyecto que tiene un archivo de origen y un archivo de encabezado.  El archivo de origen main.cpp contiene la función principal para la aplicación de consola.  El archivo de encabezado main.h contiene código para incluir el archivo de encabezado iostream.  Puede crear estos archivos de C\+\+ en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] o un editor de texto.  
  
#### Para crear los archivos de origen de C\+\+ para el proyecto  
  
1.  Cree un directorio para el proyecto.  
  
2.  Cree un archivo que se denomine main.cpp y agréguele el siguiente código:  
  
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
  
3.  Cree un archivo que se denomine main.h y agréguele el siguiente código:  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## Crear el archivo de proyecto XML de MSBuild  
 Un archivo de proyecto de [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] es un archivo XML que contiene un elemento raíz de proyecto \(\<Project\>\).  En el siguiente proyecto de ejemplo, el elemento \<Project\> contiene siete elementos secundarios:  
  
-   Tres etiquetas de grupo de elementos \(\<ItemGroup\>\) que especifican la configuración del proyecto y la plataforma, el nombre del archivo de origen y el nombre del archivo de encabezado.  
  
-   Tres etiquetas de importación \(\<Import\>\) que especifican la ubicación de la configuración de Microsoft [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
-   Una etiqueta de grupo de propiedades \(\<PropertyGroup\>\) que especifica la configuración del proyecto.  
  
#### Para crear el archivo de proyecto de MSBuild  
  
1.  Use un editor de texto para crear un archivo de proyecto denominado `myproject.vcxproj` y, a continuación, agregue el siguiente elemento \<Project\> raíz.  Inserte los elementos de los siguientes pasos del procedimiento entre las etiquetas \<Project\> raíz:  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Agregue los dos elementos secundarios \<ProjectConfiguration\> siguientes en un elemento \<ItemGroup\>.  El elemento secundario especifica las configuraciones de depuración y lanzamiento para un sistema operativo Windows de 32 bits:  
  
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
  
3.  Agregue el siguiente elemento \<Import\>, que especifica la ruta de acceso a la configuración predeterminada de C\+\+ para este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  Agregue el siguiente elemento de grupo de propiedades \(\<PropertyGroup\>\), que especifica dos propiedades del proyecto:  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  Agregue el siguiente elemento \<Import\>, que especifica la ruta de acceso a la configuración actual de C\+\+ para este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  Agregue el siguiente elemento secundario \<ClCompile\> en un elemento \<ItemGroup\>.  El elemento secundario especifica el nombre del archivo de origen de C\/C\+\+ que se va a compilar:  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  Agregue el siguiente elemento secundario \<ClInclude\> en un elemento \<ItemGroup\>.  El elemento secundario especifica el nombre del archivo de encabezado para el archivo de origen de C\/C\+\+:  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  Agregue el siguiente elemento \<Import\>, que especifica la ruta de acceso del archivo que define el destino de este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### Archivo de proyecto completo  
 En el código siguiente se muestra el archivo de proyecto completo que creó en el procedimiento anterior.  
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
    <PlatformToolset>v120</PlatformToolset>  
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
  
## Usar MSBuild para compilar el proyecto  
 Escriba en el símbolo del sistema el siguiente comando para compilar la aplicación de consola:  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] crea un directorio para los archivos de salida y, a continuación, compila y vincula el proyecto para generar el programa Myproject.exe.  Una vez que finalice el proceso de compilación, use el siguiente comando para ejecutar la aplicación:  
  
```  
myproject  
```  
  
 La aplicación debe mostrar "Hello, from MSBuild\!" en la ventana de la consola.  
  
## Personalizar el proyecto  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] permite ejecutar destinos de compilación predefinidos, aplicar propiedades definidas por el usuario y utilizar herramientas, eventos y pasos de compilación personalizados.  En esta sección se ilustran las tareas siguientes:  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con destinos de compilación.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con propiedades de compilación.  
  
-   Mediante [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con el compilador y las herramientas de 64 bits.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con conjuntos de herramientas diferentes.  
  
-   Agregar personalizaciones de [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)].  
  
### Usar MSBuild con destinos de compilación  
 Un *destino de compilación* es un conjunto de comandos predefinidos o definidos por el usuario que se pueden ejecutar durante la compilación.  Use la opción de línea de comandos target \(**\/t**\) para especificar un destino de compilación.  En el caso del proyecto de ejemplo `myproject`, el destino **clean** predefinido elimina todos los archivos de la carpeta de depuración y crea un nuevo archivo de registro.  
  
 En el símbolo del sistema, escriba el siguiente comando para limpiar `myproject`.  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### Usar MSBuild con propiedades de compilación  
 La opción de línea de comandos property \(**\/p**\) permite reemplazar una propiedad del archivo de compilación del proyecto.  En el proyecto de ejemplo `myproject`, la configuración de compilación de lanzamiento o depuración se especifica mediante la propiedad `Configuration`.  Y la propiedad `Platform` especifica el sistema operativo que está previsto que ejecute la aplicación compilada.  
  
 En el símbolo del sistema, escriba el siguiente comando para crear una compilación de depuración de la aplicación `myproject` pensada para ejecutarse en Windows de 32 bits.  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 Supongamos que el proyecto de ejemplo `myproject` también define una configuración para Windows de 64 bits y otra configuración para un sistema operativo personalizado que se denomina `myplatform`.  
  
 En el símbolo del sistema, escriba el siguiente comando para crear una versión de lanzamiento que se ejecute en Windows de 64 bits.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 En el símbolo del sistema, escriba el comando siguiente para crear una versión de lanzamiento para `myplatform`:  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### Usar MSBuild con el compilador y las herramientas de 64 bits  
 Si ha instalado [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en Windows de 64 bits, las herramientas nativas y cruzadas de 64 bits \(x64\) se instalan de forma predeterminada.  Puede configurar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para usar el compilador y las herramientas de 64 bits para compilar la aplicación si establece la propiedad `PreferredToolArchitecture`.  Esta propiedad no afecta a las propiedades de configuración del proyecto o de la plataforma.  De forma predeterminada, la versión de 32 bits de las herramientas es utilizada.  Para especificar la versión de 64 bits de compilador y de las herramientas, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después del elemento `Microsoft.Cpp.default.props` \<Import \/\>:  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 En el símbolo del sistema, escriba el siguiente comando para usa la herramienta de 64 bits para crear la aplicación.  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### Usar MSBuild con un conjunto de herramientas diferente  
 Si tiene los conjuntos de herramientas y bibliotecas de otras versiones de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] instalados, [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] puede compilar las aplicaciones para la versión actual de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] u otras versiones instaladas.  Por ejemplo, si ha instalado [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], para especificar el conjunto de herramientas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 11.0 para Windows XP, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después del elemento de Microsoft.Cpp.props `<Import />`:  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 Para recompilar su proyecto con el conjunto de herramientas de Windows XP [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 11.0, escriba cualquiera de los siguientes comandos:  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### Agregar personalizaciones de MSBuild  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] proporciona varias maneras de personalizar un proceso de compilación.  En los siguientes temas se muestra cómo agregar pasos de compilación, herramientas y eventos personalizados al proyecto de [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]:  
  
-   [Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [Cómo: Agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [Cómo: Usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)