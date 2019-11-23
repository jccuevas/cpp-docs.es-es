---
title: Archivos vcxproj. filters
ms.date: 09/25/2019
description: Use filtros archivos en proyectos de C++ Visual Studio para definir carpetas lógicas personalizadas para archivos en explorador de soluciones
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: ee44bf3d1cbe06d6c007ed8976ec384a456efca5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686927"
---
# <a name="vcxprojfilters-files"></a>Archivos vcxproj. filters

El archivo de *filtros* (\*. vcxproj. filters) es un archivo XML en formato MSBuild que se encuentra en la carpeta raíz del proyecto. Especifica los tipos de archivo que entran en la carpeta lógica de **Explorador de soluciones**. En la ilustración siguiente, los archivos *. cpp* se encuentran en el nodo **archivos de código fuente** . los *archivos. h* están en el nodo **archivos de encabezado** y los archivos *. ico* y *. RC* están en **archivos de recursos**. Esta ubicación se controla mediante el archivo de filtros.

![Carpetas lógicas en Explorador de soluciones](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Crear un archivo de filtros personalizados

Visual Studio crea este archivo automáticamente. En el caso de las aplicaciones de escritorio, las carpetas lógicas (filtros) predefinidas son: **archivos de código fuente**, **archivos de encabezado** y **archivos de recursos**. Otros tipos de proyecto, como UWP, pueden tener un conjunto diferente de carpetas predeterminadas. Visual Studio asigna automáticamente tipos de archivo conocidos a cada carpeta. Si desea crear un filtro con un nombre personalizado o un filtro que contiene tipos de archivo personalizados, puede crear su propio archivo de filtros en la carpeta raíz del proyecto o en un filtro existente. (**Las referencias** y las **dependencias externas** son carpetas especiales que no participan en el filtrado).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el archivo de filtros del ejemplo que se muestra anteriormente. Tiene una jerarquía plana; en otras palabras, no hay carpetas lógicas anidadas. El nodo `UniqueIdentifier` es opcional. Permite que las interfaces de automatización de Visual Studio encuentren el filtro. `Extensions` también es opcional. Cuando se agrega un nuevo archivo a un proyecto, se agrega al filtro de nivel superior con una extensión de archivo coincidente. Para agregar un archivo a un filtro concreto, haga clic con el botón derecho en el filtro y elija **Agregar nuevo elemento**.

La `ItemGroup` que contiene los nodos de `ClInclude` se crea cuando se inicia el proyecto por primera vez. Si va a generar sus propios archivos vcxproj, asegúrese de que todos los elementos de proyecto también tienen una entrada en el archivo de filtros. Los valores de un nodo de `ClInclude` invalidan el filtrado predeterminado en función de las extensiones de archivo. Al usar Visual Studio para agregar un nuevo elemento al proyecto, el IDE agregará una entrada de archivo individual en el archivo de filtros. El filtro no se reasigna automáticamente si cambia la extensión del archivo. 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

Para crear carpetas lógicas anidadas, declare todos los nodos en los filtros `ItemGroup` como se muestra a continuación. Cada nodo secundario debe declarar la ruta de acceso lógica completa al elemento primario superior. En el ejemplo siguiente, se debe declarar un `ParentFilter` vacío porque se hace referencia a él en nodos posteriores.

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

