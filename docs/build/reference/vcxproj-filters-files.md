---
title: Archivos Vcxproj.filters
ms.date: 09/25/2019
description: Usar archivos de filtros en proyectos de Visual Studio C++ para definir carpetas lógicas personalizadas para archivos en el Explorador de soluciones
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335935"
---
# <a name="vcxprojfilters-files"></a>archivos vcxproj.filters

El archivo\* *de filtros* ( .vcxproj.filters) es un archivo XML en formato MSBuild que se encuentra en la carpeta raíz del proyecto. Especifica qué tipos de archivo entran en qué carpeta lógica del Explorador de **soluciones.** En la siguiente ilustración, los archivos *.cpp* se encuentran en el nodo Archivos de **origen.** los archivos *.h* se encuentran en el nodo **Archivos** de encabezado y los archivos *.ico* y *.rc* se encuentran en **Archivos de**recursos . Esta ubicación se controla mediante el archivo de filtros.

![Carpetas lógicas en el Explorador de soluciones](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Creación de un archivo de filtros personalizado

Visual Studio crea este archivo automáticamente. Para aplicaciones de escritorio, las carpetas lógicas predefinidas (filtros) son: Archivos de **origen,** Archivos de **encabezado** y **Archivos de**recursos . Otros tipos de proyecto, como UWP, pueden tener un conjunto diferente de carpetas predeterminadas. Visual Studio asigna automáticamente tipos de archivo conocidos a cada carpeta. Si desea crear un filtro con un nombre personalizado o un filtro que contiene tipos de archivo personalizados, puede crear su propio archivo de filtros en la carpeta raíz del proyecto o en un filtro existente. (**Las referencias** y las **dependencias externas** son carpetas especiales que no participan en el filtrado.)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el archivo de filtros para la demostración de ejemplo anteriormente. Tiene una jerarquía plana; en otras palabras, no hay carpetas lógicas anidadas. El nodo `UniqueIdentifier` es opcional. Permite que las interfaces de automatización de Visual Studio busquen el filtro. `Extensions`también es opcional. Cuando se agrega un nuevo archivo a un proyecto, se agrega al filtro superior con una extensión de archivo coincidente. Para agregar un archivo a un filtro específico, haga clic con el botón derecho en el filtro y elija **Agregar nuevo elemento**.

El `ItemGroup` que `ClInclude` contiene los nodos se crea cuando se inicia el proyecto por primera vez. Si está generando sus propios archivos vcxproj, asegúrese de que todos los elementos del proyecto también tienen una entrada en el archivo de filtros. Los valores `ClInclude` de un nodo invalidan el filtrado predeterminado basado en extensiones de archivo. Cuando se usa Visual Studio para agregar un nuevo elemento al proyecto, el IDE agregará una entrada de archivo individual en el archivo de filtros. El filtro no se reasigna automáticamente si cambia la extensión del archivo.

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

Para crear carpetas lógicas anidadas, declare todos los nodos de los filtros `ItemGroup` como se muestra a continuación. Cada nodo secundario debe declarar la ruta de acceso lógica completa al elemento primario superior. En el ejemplo siguiente, se debe declarar un vacío `ParentFilter` porque se hace referencia a él en nodos posteriores.

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
