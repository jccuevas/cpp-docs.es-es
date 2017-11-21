---
title: 'Tutorial: Usar MSBuild para crear un proyecto de Visual C++ | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.walkthrough.createproject
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1d37e6d19d7185d98a3e58967f27d4663a65b074
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Tutorial: Usar MSBuild para crear un proyecto de Visual C++
Este tutorial muestra cómo utilizar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para compilar un proyecto de Visual C++ en un símbolo del sistema. Obtendrá información sobre cómo crear los archivos de origen de C++ y un archivo de proyecto basado en XML para una aplicación de consola de Visual C++. Después de compilar el proyecto, obtendrá información sobre cómo personalizar el proceso de compilación.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear los archivos de origen de C++ para el proyecto.  
  
-   Crear el archivo XML [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] archivo de proyecto.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para compilar el proyecto.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para personalizar el proyecto.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitas lo siguiente para poder llevar a cabo este tutorial:  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   Una descripción general de la [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] sistema.  
  
## <a name="creating-the-c-source-files"></a>Crear los archivos de origen de C++  
 En este tutorial creará un proyecto que tiene un archivo de origen y un archivo de encabezado. El archivo de origen main.cpp contiene la función main de la aplicación de consola. El archivo de encabezado main.h contiene código para incluir el archivo de encabezado iostream. Puede crear estos archivos C++ mediante [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] o un editor de texto.  
  
#### <a name="to-create-the-c-source-files-for-your-project"></a>Para crear los archivos de origen de C++ para el proyecto  
  
1.  Cree un directorio para el proyecto.  
  
2.  Crear un archivo que se denomine main.cpp y agregue el código siguiente a este archivo:  
  
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
  
3.  Crear un archivo que se denomine main.h y agregue el código siguiente a este archivo:  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## <a name="creating-the-xml-msbuild-project-file"></a>Crear el archivo de proyecto de MSBuild XML  
 Un [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] archivo de proyecto es un archivo XML que contiene un elemento raíz del proyecto (\<proyecto >). En el proyecto de ejemplo siguiente, la \<proyecto > elemento contiene siete elementos secundarios:  
  
-   Tres etiquetas de grupo de elementos (\<ItemGroup >) que especifican la configuración del proyecto y plataforma, nombre de archivo de origen y el nombre del archivo de encabezado.  
  
-   Tres importación etiquetas (\<Importar >) que especifican la ubicación de configuración de Microsoft Visual C++.  
  
-   Una etiqueta de grupo de propiedad (\<PropertyGroup >) que especifica la configuración del proyecto.  
  
#### <a name="to-create-the-msbuild-project-file"></a>Para crear el archivo de proyecto de MSBuild  
  
1.  Utilice un editor de texto para crear un archivo de proyecto que se denomina `myproject.vcxproj`y, a continuación, agregue la siguiente raíz \<proyecto > elemento. Inserte los elementos en los siguientes pasos del procedimiento entre la raíz \<proyecto > etiquetas:  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Agregue las dos siguientes \<ProjectConfiguration > elementos secundarios en un \<ItemGroup > elemento. El elemento secundario especifica debug y release configuraciones para un sistema operativo de Windows de 32 bits:  
  
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
  
3.  Agregue las siguientes \<importación / > elemento que especifica la ruta de acceso de la configuración predeterminada de C++ para este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  Agregue el siguiente elemento de grupo de propiedades (\<PropertyGroup >) que especifica dos propiedades del proyecto:  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  Agregue las siguientes \<importación / > elemento que especifica la ruta de acceso de la configuración actual de C++ para este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  Agregue el siguiente \<ClCompile > elemento secundario de un \<ItemGroup > elemento. El elemento secundario especifica el nombre del archivo de origen de C o C++ para compilar:  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  Agregue el siguiente \<ClInclude > elemento secundario de un \<ItemGroup > elemento. El elemento secundario especifica el nombre del archivo de encabezado para el archivo de código fuente de C y C++:  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  Agregue las siguientes \<importación > elemento que especifica la ruta de acceso del archivo que define el objetivo de este proyecto:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### <a name="complete-project-file"></a>Archivo de proyecto completo  
 El código siguiente muestra el archivo de proyecto completo que creó en el procedimiento anterior.  
  
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
  
## <a name="using-msbuild-to-build-your-project"></a>Usar MSBuild para compilar el proyecto  
 Escriba el siguiente comando en el símbolo del sistema para compilar la aplicación de consola:  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]crea un directorio para los archivos de salida y, a continuación, compila y vincula el proyecto para generar el programa Myproject.exe. Al finalizar el proceso de compilación, use el comando siguiente para ejecutar la aplicación:  
  
```  
myproject  
```  
  
 La aplicación debería mostrar "¡Hello, de MSBuild!" en la ventana de la consola.  
  
## <a name="customizing-your-project"></a>Personalizar el proyecto  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]le permite ejecutar destinos de compilación predefinidos, aplicar propiedades definidas por el usuario y usar herramientas personalizadas, eventos, y pasos de compilación. En esta sección se muestra las tareas siguientes:  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con destinos de compilación.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con propiedades de compilación.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con las herramientas y el compilador de 64 bits.  
  
-   Usar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] con diferentes conjuntos de herramientas.  
  
-   Agregar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] personalizaciones.  
  
### <a name="using-msbuild-with-build-targets"></a>Usar MSBuild con destinos de compilación  
 A *crear destino* es un conjunto de comandos predefinidos o definidos por el usuario que se pueden ejecutar durante la compilación. Utilice la opción de línea de comandos de destino (**/t**) para especificar un destino de compilación. En el caso de los `myproject` proyecto de ejemplo, predefinido **limpia** elimina todos los archivos en la carpeta de depuración y crea un nuevo archivo de registro de destino.  
  
 En el símbolo del sistema, escriba el siguiente comando para limpiar `myproject`.  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### <a name="using-msbuild-with-build-properties"></a>Usar MSBuild con propiedades de compilación  
 La opción de línea de comandos de la propiedad (**/p**) permite reemplazar una propiedad en el archivo de compilación del proyecto. En el `myproject` configuración de compilación de proyecto, la versión o de depuración de ejemplo se especifica mediante el `Configuration` propiedad. Y el sistema operativo que está diseñado para que se ejecute la aplicación compilada se especifican mediante el `Platform` propiedad.  
  
 En el símbolo del sistema, escriba el comando siguiente para crear una compilación de depuración de la `myproject` aplicación que está diseñada para ejecutarse en Windows de 32 bits.  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 Se asume que el `myproject` ejemplo proyecto también define una configuración para Windows de 64 bits y otra configuración para un sistema operativo personalizado denominado `myplatform`.  
  
 En el símbolo del sistema, tipo el siguiente comando para crear una versión de compilación que se ejecuta en Windows de 64 bits.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 En el símbolo del sistema, escriba el comando siguiente para crear una versión de lanzamiento para `myplatform`.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Usar MSBuild con el compilador de 64 bits y herramientas  
 Si ha instalado Visual C++ en Windows de 64 bits, de forma predeterminada, se instalan los x64 64 bits nativa y cruzada herramientas. Puede configurar [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] para usar el compilador de 64 bits y herramientas para compilar la aplicación mediante el establecimiento del `PreferredToolArchitecture` propiedad. Esta propiedad no afecta a las propiedades de configuración o la plataforma del proyecto. De forma predeterminada, se utiliza la versión de 32 bits de las herramientas. Para especificar la versión de 64 bits del compilador y herramientas, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj después de la `Microsoft.Cpp.default.props` \<importación / > elemento:  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 En el símbolo del sistema, escriba el comando siguiente para usar las herramientas de 64 bits para compilar la aplicación.  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="using-msbuild-with-a-different-toolset"></a>Usar MSBuild con un conjunto de herramientas diferente  
 Si tiene los conjuntos de herramientas y bibliotecas para otras versiones de Visual C++ instalado, [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] puede compilar aplicaciones para cada uno con la versión actual de Visual C++ o para las demás versiones instaladas. Por ejemplo, si ha instalado [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], para especificar el conjunto de herramientas 11.0 de Visual C++ para Windows XP, agregue el siguiente elemento de grupo de propiedades al archivo de proyecto Myproject.vcxproj tras el Microsoft.Cpp.props `<Import />` elemento:  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 Para volver a crear el proyecto con el conjunto de herramientas de Visual C++ 11.0 Windows XP, escriba cualquiera de los siguientes comandos:  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### <a name="adding-msbuild-customizations"></a>Agregar personalizaciones de MSBuild  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]proporciona varias maneras de personalizar el proceso de compilación. Los temas siguientes muestra cómo agregar pasos de compilación personalizada, herramientas y eventos a su [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] proyecto:  
  
-   [Procedimiento para agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [Procedimiento para usar eventos de compilación en proyectos de MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)