---
title: estructura de archivos .vcxproj y .props | Documentos de Microsoft
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d48b16d9a4250de8c8c3dfef62fdcfb5c1434960
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="vcxproj-and-props-file-structure"></a>estructura del archivo .vcxproj y .props

MSBuild es el sistema de proyecto de forma predeterminada en Visual Studio; Cuando eliges **archivo | Nuevo proyecto** en Visual C++ está creando un proyecto de MSBuild cuya configuración se almacena en un archivo de proyecto XML con la extensión `.vcxproj`. El archivo de proyecto también puede importar archivos .props y .targets donde se almacena la configuración. En la mayoría de los casos, nunca debe editar manualmente el archivo de proyecto y, en realidad debería no modificarla manualmente a menos que tenga un buen conocimiento de MSBuild. Siempre que sea posible debe usar las páginas de propiedades de Visual Studio para modificar la configuración de proyecto (vea [trabajar con configuraciones de proyecto](working-with-project-properties.md). Sin embargo, en algunos casos deberá modificar manualmente una proyecto archivo u hoja de propiedades. En esos escenarios, este artículo contiene información básica acerca de la estructura del archivo.

**Importante:**

Si decide editar manualmente un archivo .vcxproj, tener en cuenta estos hechos:

1. La estructura del archivo debe seguir un formulario prescrito, que se describe en este artículo.

1. Actualmente el sistema de proyectos de Visual C++ no admite caracteres comodín en elementos de proyecto. Por ejemplo, esto no se admite:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. El sistema de proyectos de Visual C++ no admite actualmente las macros en rutas de acceso de elemento de proyecto. Por ejemplo, esto no se admite:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

1. Para disponer de propiedades del proyecto agregado, eliminado o modificado cuando edita en correctamente la **propiedades del proyecto** cuadro de diálogo, el archivo debe contener grupos independientes para cada configuración de proyecto y las condiciones deben tener este formato:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Cada propiedad debe especificarse en el grupo con la etiqueta correcta, tal como se especifica en el archivo de regla de propiedad. Para obtener más información, consulte [archivos de regla de xml de página de propiedades](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>elementos del archivo .vcxproj

Puede inspeccionar el contenido de un archivo .vcxproj utilizando cualquier texto o editor XML. Puede verlo en Visual Studio con el botón secundario en el proyecto en el Explorador de soluciones, elija **descargar el proyecto** y, a continuación, elija **Foo.vcxproj editar**.

Lo primero que debe tener en cuenta es que los elementos de nivel superior aparecen en un orden concreto. Por ejemplo:

- la mayoría de los grupos de propiedades y grupos de definición de elemento se producen después de la importación de Microsoft.Cpp.Default.props.
- todos los destinos se importan al final del archivo.
- Hay varios grupos de propiedad, cada uno con una etiqueta única, y se producen en un orden concreto.

El orden de los elementos en el archivo de proyecto es muy importante, porque MSBuild se basa en un modelo de evaluación secuencial.  Si el archivo de proyecto, incluidos todos los .props importados y los archivos .targets, consta de varias definiciones de una propiedad, la última definición invalida los anteriores. En el ejemplo siguiente, se establecerá el valor "xyz" durante la compilación porque encuentre lo último durante su evaluación del motor de MSBUild.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

El fragmento de código siguiente muestra un archivo .vcxproj mínima. Cualquier archivo .vcxproj generado por Visual Studio contendrá estos elementos de MSBuild de nivel superior y aparecerán en este orden (aunque pueden contener varias copias de cada elemento de nivel superior). Tenga en cuenta que `Label` los atributos son etiquetas arbitrarias que solo se usan Visual Studio como paneles de señalización para su edición; no tienen ninguna otra función.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
   <ItemGroup Label="ProjectConfigurations" />
   <PropertyGroup Label="Globals" />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
   <PropertyGroup Label="Configuration" />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
   <ImportGroup Label="ExtensionSettings" />
   <ImportGroup Label="PropertySheets" />
   <PropertyGroup Label="UserMacros" />
   <PropertyGroup />
   <ItemDefinitionGroup />
   <ItemGroup />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
   <ImportGroup Label="ExtensionTargets" />
 </Project>
```

Las secciones siguientes describen el propósito de cada uno de estos elementos y por qué se ordenan de esta forma:

### <a name="project-element"></a>Project (elemento)

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project`es el nodo raíz. Especifica la versión de MSBuild que se va a usar y también el destino predeterminado que se ejecuta cuando se pasa este archivo a MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>Elemento ProjectConfigurations ItemGroup

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations`contiene la descripción de la configuración de proyecto. Algunos ejemplos son depuración | Win32, versión | Win32, depuración | ARM y así sucesivamente. Muchas configuraciones de proyecto son específicas de una configuración determinada. Por ejemplo, probablemente deseará establecer las propiedades de optimización de una versión de lanzamiento pero no en una compilación de depuración.

El `ProjectConfigurations` grupo de elementos no se utiliza en tiempo de compilación. El IDE de Visual Studio se requiere para cargar el proyecto. Este grupo de elementos se puede mover a un archivo .props e importado en el archivo .vcxproj. Sin embargo, en ese caso, si necesita agregar o quitar configuraciones, debe editar manualmente el archivo .props; no se puede usar el IDE.

### <a name="projectconfiguration-elements"></a>Elementos de configuración del proyecto

El siguiente fragmento muestra una configuración de proyecto. En este ejemplo ' depurar | x 64' es el nombre de configuración. El nombre de la configuración de proyecto debe estar en el formato $(Configuration)|$(Platform). Un nodo de configuración del proyecto puede tener dos propiedades: configuración y plataforma. Dichas propiedades se establecerá automáticamente con los valores especificados aquí cuando la configuración está activa.

   ```xml
   <ProjectConfiguration Include="Debug|x64">
     <Configuration>Debug</Configuration>
     <Platform>x64</Platform>
   </ProjectConfiguration>
   ```

El IDE espera encontrar una configuración de proyecto a cualquier combinación de valores de configuración y la plataforma que se utilizan en todos los elementos de configuración del proyecto. A menudo, esto significa que un proyecto puede tener las configuraciones de proyecto no tenga sentido para satisfacer este requisito. Por ejemplo, si un proyecto tiene estas configuraciones:

- Debug|Win32
- Retail|Win32
- Optimización de 32 bits especial | Win32

a continuación, también debe tener estas configuraciones, incluso aunque no tenga sentida para x64 "Optimización de 32 bits especial":

- Depuración|x64
- Retail|x64
- Optimización de 32 bits especial | x64

Puede deshabilitar la compilación e implementar los comandos de configuración en el **solución Configuration Manager**.

### <a name="globals-propertygroup-element"></a>Elemento Globals PropertyGroup

```xml
 <PropertyGroup Label="Globals" />
```

`Globals`contiene la configuración de nivel de proyecto, como ProjectGuid y RootNamespace, ApplicationType / ApplicationTypeRevision. Las dos últimas suelen definen el sistema operativo de destino. Un proyecto solo puede destinar un único sistema operativo debido al hecho de que las referencias y los elementos de proyecto no pueden tener condiciones actualmente. Estas propiedades son normalmente no se reemplaza en otro lugar en el archivo de proyecto. Este grupo no es dependiente de la configuración y, por tanto, normalmente solo un grupo de funciones globales existe en el archivo de proyecto.

### <a name="microsoftcppdefaultprops-import-element"></a>Elemento de importación de Microsoft.Cpp.default.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

El **Microsoft.Cpp.default.props** hoja de propiedades se incluye con Visual Studio y no se puede modificar. Contiene la configuración predeterminada para el proyecto. Los valores predeterminados pueden variar según el ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Elementos de configuración PropertyGroup

```xml
<PropertyGroup Label="Configuration" />
```

A `Configuration` grupo de propiedades tiene una condición de configuración adjunta (como `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) y se pone en varias copias, uno por cada configuración. Este grupo de propiedades hospeda las propiedades que se establecen para una configuración concreta. Propiedades de configuración incluyen PlatformToolset y controlar la inclusión de hojas de propiedades del sistema en **Microsoft.Cpp.props**. Por ejemplo, si se define la propiedad `<CharacterSet>Unicode</CharacterSet>`, a continuación, la hoja de propiedades del sistema **microsoft. CPP.unicodesupport.props** se van a incluir. Si examina **Microsoft.Cpp.props**, verá la línea: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`.

### <a name="microsoftcppprops-import-element"></a>Elemento de importación de Microsoft.Cpp.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

El **Microsoft.Cpp.props** hoja de propiedades (directamente o a través de las importaciones) define los valores predeterminados para muchas propiedades específicas de la herramienta como las propiedades de optimización y nivel de advertencia del compilador, Nombrebibliotecatipos la herramienta MIDL propiedad y así sucesivamente. También importa varias hojas de propiedades de sistema en función de qué propiedades de configuración se definen en el grupo de propiedades inmediatamente anterior.

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings ImportGroup (elemento)

```xml
<ImportGroup Label="ExtensionSettings" />
```

El `ExtensionSettings` grupo contiene las importaciones para las hojas de propiedades que forman parte de las personalizaciones de compilación. Una personalización de compilación se define por hasta tres archivos: un archivo .targets, un archivo .props y un archivo XML. Este grupo de importación contiene las importaciones para el archivo .props.

### <a name="propertysheets-importgroup-elements"></a>Elementos de PropertySheets ImportGroup

```xml
<ImportGroup Label="PropertySheets" />
```

El `PropertySheets` grupo contiene las importaciones de hojas de propiedades de usuario. Se trata de las hojas de propiedades que se agregan mediante la vista del Administrador de propiedades en Visual Studio. El orden en que se muestran estas importaciones es importante y se refleja en el Administrador de propiedades. El archivo de proyecto normalmente contiene varias instancias de este tipo de grupo de importación, uno para cada configuración de proyecto.

### <a name="usermacros-propertygroup-element"></a>Elemento UserMacros PropertyGroup

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros`contiene propiedades que se crean como las variables que se utilizan para personalizar el proceso de compilación. Por ejemplo, puede definir una macro de usuario para definir la ruta de acceso de salida personalizada como $(CustomOutputPath) y úsela para definir otras variables. Este grupo de propiedades contiene estas propiedades. Tenga en cuenta que en Visual Studio, este grupo no se rellena en el archivo de proyecto porque Visual C++ no admite las macros de usuario para las configuraciones. Macros de usuario se admiten en las hojas de propiedades.

### <a name="per-configuration-propertygroup-elements"></a>Elementos de configuración por configuración PropertyGroup

```xml
<PropertyGroup />
```

Hay varias instancias de este grupo de propiedades, uno por cada configuración para todas las configuraciones de proyecto. Cada grupo de propiedades debe tener una condición de configuración adjunta. Si faltan las configuraciones, el **propiedades del proyecto** cuadro de diálogo no funcionará correctamente. A diferencia de los grupos de propiedad anteriores, éste no tiene una etiqueta. Este grupo contiene la configuración de nivel de configuración de proyecto. Esta configuración se aplica a todos los archivos que forman parte del grupo de elementos especificado. Definición de elemento de personalización de compilación se inicializan los metadatos aquí.

Este PropertyGroup debe venir detrás de `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` y no debe haber ningún otro PropertyGroup sin una etiqueta delante de él (en caso contrario, la edición de propiedades del proyecto no funcionará correctamente).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Elementos de ItemDefinitionGroup por configuración

```xml
 <ItemDefinitionGroup />
```

Contiene las definiciones de elemento. Éstas deben seguir las mismas reglas de condiciones que los elementos PropertyGroup según la configuración de menor de etiqueta.

### <a name="itemgroup-elements"></a>Elementos de ItemGroup

```xml
<ItemGroup />
```

Contiene los elementos (archivos de código fuente, etc.) en el proyecto. No se admiten condiciones para elementos de proyecto (es decir, tipos de elemento que se tratan como elementos de proyecto mediante las definiciones de reglas).

Los metadatos deben tener las condiciones de configuración para cada configuración, incluso si son los mismos. Por ejemplo:

   ```xml
   <ItemGroup>
     <ClCompile Include="stdafx.cpp">
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
     </ClCompile>
   </ItemGroup>
   ```

Actualmente el sistema de proyectos de Visual C++ no admite caracteres comodín en elementos de proyecto.

   ```xml
   <ItemGroup>
     <ClCompile Include="*.cpp"> <!--Error-->
   </ItemGroup>
   ```

El sistema de proyectos de Visual C++ no admite actualmente las macros en elementos de proyecto.

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
   </ItemGroup>
   ```

Las referencias se especifican en un ItemGroup y tienen estas limitaciones:

- Las referencias no son compatibles con las condiciones.
- Metadatos de las referencias no son compatibles con las condiciones.

### <a name="microsoftcpptargets-import-element"></a>Elemento Microsoft.Cpp.targets Import

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Define (directamente o a través de las importaciones) destinos de Visual C++ como compilar, limpiar, etcetera.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets ImportGroup (elemento)

```xml
<ImportGroup Label="ExtensionTargets" />
```

Este grupo contiene las importaciones para los archivos de destino de la personalización de compilación.

## <a name="impact-of-incorrect-ordering"></a>Impacto de ordenación incorrecto

El IDE de Visual Studio depende en el archivo de proyecto con que la ordenación se ha descrito anteriormente. Por ejemplo, cuando se define un valor de propiedad en las páginas de propiedades, el IDE normalmente colocará la definición de propiedad en el grupo de propiedades con la etiqueta vacía. Esto garantiza que los valores predeterminados pone en las hojas de propiedades del sistema son reemplazados por valores definidos por el usuario. De forma similar, los archivos de destino se importan al final, puesto que consumen las propiedades definidas anteriormente y ya que generalmente no definen propiedades en Sí. Del mismo modo, se importan las hojas de propiedades de usuario después de las hojas de propiedades del sistema (incluido a través de **Microsoft.Cpp.props**). Esto garantiza que el usuario puede invalidar los valores predeterminados que se pone las hojas de propiedades del sistema.

Si un archivo .vcxproj no sigue este diseño, los resultados de compilación no pueden ser los esperados. Por ejemplo, si importa una hoja de propiedades del sistema por error después de las hojas de propiedades definidas por el usuario, la configuración de usuario serán reemplazada por las hojas de propiedades del sistema.

Incluso la experiencia de tiempo de diseño del IDE depende hasta cierto punto en el orden correcto de los elementos. Por ejemplo, si el archivo .vcxproj no tiene la `PropertySheets` grupo de importación, el IDE no pueda determinar dónde se debe colocar una nueva hoja de propiedades que el usuario ha creado en **Administrador de propiedades**. Esto podría resultar en una hoja de usuario que se va a reemplazar por una hoja de sistema. Aunque la heurística utilizada por el IDE puede tolerar incoherencias poco importantes en el diseño del archivo .vcxproj, se recomienda encarecidamente no se desvíe de la estructura que se muestra anteriormente en este artículo.

## <a name="how-the-ide-uses-element-labels"></a>Cómo el IDE usa etiquetas de elemento

En el IDE, al establecer el **useOfATL ()** propiedad en la página de propiedades general, se escribe en el grupo de propiedades de configuración en el archivo de proyecto, mientras que la **TargetName** propiedad en la misma página de propiedades se escribe en el grupo de propiedades de etiqueta menos según la configuración. Visual Studio busca en el archivo xml de la página de propiedades para ver la información sobre dónde escriben cada propiedad. Para el **General** página de propiedades (suponiendo que tenga una versión en inglés de Visual Studio Enterprise Edition), que el archivo esté `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. El archivo de reglas XML de página de propiedades define la información estática sobre una regla y todas sus propiedades. Una parte de este tipo de información es la posición preferida de una propiedad de regla en el archivo de destino (es decir, el archivo donde se escribirá el valor). La posición preferida es especificada por el atributo de etiqueta de los elementos del archivo de proyecto.

## <a name="property-sheet-layout"></a>Diseño de la hoja de propiedades

El siguiente fragmento XML es un diseño mínimo de un archivo de hoja (.props) de la propiedad. Es similar a un archivo .vcxproj, y la funcionalidad de los elementos props puede deducirse de la explicación anterior.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Para realizar su propia hoja de propiedades, copie uno de los archivos .props en la carpeta VCTargets y modificarlo para sus fines. Para Visual Studio de 2017 Enterprise edition, es la ruta de acceso predeterminada VCTargets `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](working-with-project-properties.md)  
[Archivos XML de página de propiedades](property-page-xml-files.md)  
