---
title: Estructura de los archivos .vcxproj y .props | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 957d9e1063c71e342339eb4e6a6c913eeb5a8f64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374093"
---
# <a name="vcxproj-and-props-file-structure"></a>Estructura de los archivos .vcxproj y .props

[MSBuild](../build/msbuild-visual-cpp.md) es el sistema de proyectos predeterminado en Visual Studio; cuando se selecciona **Archivo** > **Nuevo proyecto** en Visual C++ se crea un proyecto de MSBuild cuya configuración se almacena en un archivo de proyecto XML con la extensión `.vcxproj`. El archivo de proyecto también puede importar archivos .props y .targets en los que se puede almacenar la configuración. En la mayoría de los casos, nunca tendrá que editar manualmente el archivo de proyecto y, en realidad, no debería modificarlo de forma manual a menos que tenga un buen conocimiento de MSBuild. Siempre que sea posible, debe usar las páginas de propiedades de Visual Studio para modificar la configuración del proyecto (vea [Trabajar con propiedades de proyecto](working-with-project-properties.md). Pero en algunos casos es posible que tenga que modificar manualmente un archivo de proyecto o una hoja de propiedades. Para esos escenarios, este artículo contiene información básica sobre la estructura del archivo.

**Importante:**

Si decide editar manualmente un archivo .vcxproj, tenga en cuenta estos hechos:

1. La estructura del archivo debe seguir un formato establecido, que se describe en este artículo.

1. En la actualidad, el sistema de proyectos de Visual C++ no admite caracteres comodín en los elementos de proyecto. Por ejemplo, esto no se admite:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. En la actualidad, el sistema de proyectos de Visual C++ no admite las macros en las rutas de acceso de los elementos de proyecto. Por ejemplo, esto no se admite:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "Incompatible" significa que no se garantiza que las macros funcionen para todas las operaciones del IDE. Las macros que no cambian su valor en distintas configuraciones deberían funcionar, pero podrían no conservarse si un elemento se mueve a un proyecto o filtro diferente. Las macros que cambian su valor para las distintas configuraciones causarán problemas porque el IDE no espera que las rutas de acceso a elementos de proyecto sean diferentes para configuraciones de proyecto distintas.

1. Para que las propiedades del proyecto se agreguen, eliminen o modifiquen de manera correcta cuando se edita en el cuadro de diálogo **Propiedades del proyecto**, el archivo debe contener grupos independientes para cada configuración de proyecto y las condiciones deben tener este formato:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Cada propiedad se debe especificar en el grupo con la etiqueta correcta, como se especifica en el archivo de regla de la propiedad. Para obtener más información, vea [Archivos de regla XML de página de propiedades](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>Elementos del archivo .vcxproj

Puede inspeccionar el contenido de un archivo .vcxproj mediante cualquier editor XML o de texto. Puede verlo en Visual Studio si hace clic con el botón derecho en el proyecto en el Explorador de soluciones, selecciona **Descargar proyecto** y después **Editar Foo.vcxproj**.

Lo primero que debe tener en cuenta es que los elementos de nivel superior aparecen en un orden concreto. Por ejemplo:

- La mayoría de los grupos de propiedades y grupos de definición de elemento aparecen después de la importación de Microsoft.Cpp.Default.props.

- Todos los destinos se importan al final del archivo.

- Hay varios grupos de propiedad, cada uno con una etiqueta única, y aparecen en un orden concreto.

El orden de los elementos en el archivo de proyecto es muy importante, porque MSBuild se basa en un modelo de evaluación secuencial.  Si el archivo de proyecto, incluidos todos los archivos .props y .targets importados, consta de varias definiciones de una propiedad, la última definición invalida las anteriores. En el ejemplo siguiente, se establecerá el valor "xyz" durante la compilación porque el motor de MSBUild lo encuentra en último lugar durante su evaluación.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

En el fragmento de código siguiente se muestra un archivo .vcxproj mínimo. Cualquier archivo .vcxproj generado por Visual Studio contendrá estos elementos de MSBuild de nivel superior y aparecerán en este orden (aunque pueden contener varias copias de cada elemento de nivel superior de ese tipo). Tenga en cuenta que los atributos `Label` son etiquetas arbitrarias que solo se usan en Visual Studio como señalizadores para la edición; no tienen ninguna otra función.

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

En las secciones siguientes se describe el propósito de cada uno de estos elementos y por qué se ordenan de esta forma:

### <a name="project-element"></a>Elemento de proyecto

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` es el nodo raíz. Especifica la versión de MSBuild que se va a usar y también el destino predeterminado que se va a ejecutar cuando este archivo se pasa a MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>Elemento ItemGroup ProjectConfigurations

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` contiene la descripción de la configuración del proyecto. Algunos ejemplos son Debug|Win32, Release|Win32, Debug|ARM y así sucesivamente. Muchas configuraciones de proyecto son específicas de una configuración determinada. Por ejemplo, es probable que le interese establecer propiedades de optimización para una compilación de versión pero no para una compilación de depuración.

El grupo de elementos `ProjectConfigurations` no se usa en tiempo de compilación. El IDE de Visual Studio lo requiere para poder cargar el proyecto. Este grupo de elementos se puede mover a un archivo .props e importar al archivo .vcxproj. Pero en ese caso, si necesita agregar o quitar configuraciones, debe editar manualmente el archivo .props; no se puede usar el IDE.

### <a name="projectconfiguration-elements"></a>Elementos ProjectConfiguration

En el fragmento de código siguiente se muestra una configuración de proyecto. En este ejemplo, "Debug|x64" es el nombre de la configuración. El nombre de la configuración de proyecto debe estar en el formato $(Configuración)|$(Plataforma). Un nodo de configuración del proyecto puede tener dos propiedades: Configuration y Platform. Estas propiedades se establecerán de manera automática con los valores especificados aquí cuando la configuración está activa.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

El IDE espera encontrar una configuración de proyecto para cualquier combinación de valores Configuration y Configuration que se usen en todos los elementos ProjectConfiguration. A menudo, esto significa que es posible que un proyecto tenga configuraciones de proyecto sin sentido para satisfacer este requisito. Por ejemplo, si un proyecto tiene estas configuraciones:

- Debug|Win32

- Retail|Win32

- Optimización de 32 bits especial|Win32

también debe tener estas configuraciones, aunque "Optimización de 32 bits especial" no tenga sentido para x64:

- Depuración|x64

- Retail|x64

- Optimización de 32 bits especial|x64

Puede deshabilitar los comandos de compilación e implementación para cualquier configuración en el **Administrador de configuración de soluciones**.

### <a name="globals-propertygroup-element"></a>Elemento PropertyGroup Globals

```xml
<PropertyGroup Label="Globals" />
```

`Globals` contiene la configuración de nivel de proyecto, como ProjectGuid, RootNamespace y ApplicationType/ ApplicationTypeRevision. Las dos últimas suelen definir el sistema operativo de destino. Un proyecto solo puede tener como destino un único sistema operativo porque las referencias y los elementos de proyecto no pueden tener condiciones en la actualidad. Normalmente estas propiedades no se reemplazan en otros lugares del archivo de proyecto. Este grupo no depende de la configuración y, por tanto, normalmente solo hay un grupo Globals en el archivo de proyecto.

### <a name="microsoftcppdefaultprops-import-element"></a>Elemento de importación Microsoft.Cpp.default.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

La hoja de propiedades **Microsoft.Cpp.default.props** se incluye con Visual Studio y no se puede modificar. Contiene la configuración predeterminada para el proyecto. Es posible que los valores predeterminados varíen según el valor de ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Elementos de configuración PropertyGroup

```xml
<PropertyGroup Label="Configuration" />
```

Un grupo de propiedades `Configuration` tiene una condición de configuración adjunta (como `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) y hay varias copias, una por cada configuración. Este grupo de propiedades hospeda las propiedades que se establecen para una configuración concreta. Las propiedades de configuración incluyen PlatformToolset y también controlan la inclusión de hojas de propiedades del sistema en **Microsoft.Cpp.props**. Por ejemplo, si se define la propiedad `<CharacterSet>Unicode</CharacterSet>`, se incluirá la hoja de propiedades del sistema **microsoft.Cpp.unicodesupport.props**. Si examina **Microsoft.Cpp.props**, verá la línea: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`.

### <a name="microsoftcppprops-import-element"></a>Elemento de importación Microsoft.Cpp.props

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

En la hoja de propiedades **Microsoft.Cpp.props** (directamente o a través de las importaciones) se definen los valores predeterminados para muchas propiedades específicas de la herramienta como las propiedades de optimización y nivel de advertencia del compilador, la propiedad TypeLibraryName de la herramienta MIDL y así sucesivamente. También importa varias hojas de propiedades del sistema en función de las propiedades de configuración que se definan en el grupo de propiedades inmediatamente anterior.

### <a name="extensionsettings-importgroup-element"></a>Elemento ImportGroup ExtensionSettings

```xml
<ImportGroup Label="ExtensionSettings" />
```

El grupo `ExtensionSettings` contiene las importaciones para las hojas de propiedades que forman parte de las personalizaciones de compilación. Una personalización de compilación se define por hasta tres archivos: un archivo .targets, un archivo .props y un archivo .xml. Este grupo de importación contiene las importaciones para el archivo .props.

### <a name="propertysheets-importgroup-elements"></a>Elementos ImportGroup PropertySheets

```xml
<ImportGroup Label="PropertySheets" />
```

El grupo `PropertySheets` contiene las importaciones de hojas de propiedades de usuario. Se trata de las hojas de propiedades que se agregan mediante la vista Administrador de propiedades en Visual Studio. El orden en que se muestran estas importaciones es importante y se refleja en el Administrador de propiedades. El archivo de proyecto normalmente contiene varias instancias de este tipo de grupo de importación, una para cada configuración de proyecto.

### <a name="usermacros-propertygroup-element"></a>Elemento PropertyGroup UserMacros

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` contiene propiedades que se crean como variables que se usan para personalizar el proceso de compilación. Por ejemplo, se puede definir una macro de usuario para definir la ruta de acceso de salida personalizada como $(CustomOutputPath) y usarla para definir otras variables. Este grupo de propiedades contiene este tipo de propiedades. Tenga en cuenta que en Visual Studio, este grupo no se rellena en el archivo de proyecto porque Visual C++ no admite las macros de usuario para las configuraciones. Las macros de usuario se admiten en las hojas de propiedades.

### <a name="per-configuration-propertygroup-elements"></a>Elementos PropertyGroup por cada configuración

```xml
<PropertyGroup />
```

Hay varias instancias de este grupo de propiedades, una por cada configuración para todas las configuraciones de proyecto. Cada grupo de propiedades debe tener una condición de configuración adjunta. Si falta alguna configuración, el cuadro de diálogo **Propiedades del proyecto** no funcionará correctamente. A diferencia de los grupos de propiedades anteriores, este no tiene una etiqueta. Este grupo contiene la configuración de nivel de configuración del proyecto. Esta configuración se aplica a todos los archivos que forman parte del grupo de elementos especificado. Los metadatos de definición del elemento de personalización de compilación se inicializan aquí.

Este grupo de propiedades debe aparecer después `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` y no debe haber ningún otro sin una etiqueta por delante (en caso contrario, la edición de propiedades del proyecto no funcionará correctamente).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Elementos ItemDefinitionGroup por cada configuración

```xml
<ItemDefinitionGroup />
```

Contiene definiciones de elementos. Estas deben seguir las mismas reglas de condiciones que los elementos PropertyGroup sin etiqueta para cada configuración.

### <a name="itemgroup-elements"></a>Elementos ItemGroup

```xml
<ItemGroup />
```

Contiene los elementos (archivos de código fuente, etc.) del proyecto. No se admiten condiciones para los elementos de proyecto (es decir, los tipos de elemento que se tratan como elementos de proyecto mediante las definiciones de reglas).

Los metadatos deben tener condiciones de configuración para cada configuración, incluso si son las mismas. Por ejemplo:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

En la actualidad, el sistema de proyectos de Visual C++ no admite caracteres comodín en los elementos de proyecto.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

En la actualidad, el sistema de proyectos de Visual C++ no admite las macros en los elementos de proyecto.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Las referencias se especifican en un ItemGroup y tienen estas limitaciones:

- Las referencias no son compatibles con las condiciones.

- Las metadatos de referencias no son compatibles con las condiciones.

### <a name="microsoftcpptargets-import-element"></a>Elemento de importación Microsoft.Cpp.targets

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Define (directamente o a través de las importaciones) destinos de Visual C++ como compilación, limpieza, etc.

### <a name="extensiontargets-importgroup-element"></a>Elemento ImportGroup ExtensionTargets

```xml
<ImportGroup Label="ExtensionTargets" />
```

Este grupo contiene las importaciones para los archivos de destino de personalización de compilación.

## <a name="impact-of-incorrect-ordering"></a>Impacto de la ordenación incorrecta

El IDE de Visual Studio depende de que el archivo de proyecto tenga la ordenación descrita anteriormente. Por ejemplo, cuando se define un valor de propiedad en las páginas de propiedades, el IDE normalmente colocará la definición de propiedad en el grupo de propiedades con la etiqueta vacía. Esto garantiza que los valores predeterminados de las hojas de propiedades del sistema se reemplazan por valores definidos por el usuario. De forma similar, los archivos de destino se importan al final, ya que consumen las propiedades definidas anteriormente y porque generalmente no definen propiedades propias. Del mismo modo, las hojas de propiedades de usuario se importan después de las hojas de propiedades del sistema (incluidas a través de **Microsoft.Cpp.props**). Esto garantiza que el usuario pueda invalidar los valores predeterminados incluidos en las hojas de propiedades del sistema.

Si un archivo .vcxproj no sigue este diseño, es posible que los resultados de la compilación no sean los esperados. Por ejemplo, si importa una hoja de propiedades del sistema por error después de las hojas de propiedades definidas por el usuario, la configuración del usuario se reemplazará por las hojas de propiedades del sistema.

Incluso la experiencia de tiempo de diseño del IDE depende hasta cierto punto del orden correcto de los elementos. Por ejemplo, si el archivo .vcxproj no tiene el grupo de importación `PropertySheets`, es posible que el IDE no pueda determinar dónde se debe colocar una hoja de propiedades nueva que el usuario ha creado en el **Administrador de propiedades**. Como resultado, una hoja del sistema podría reemplazar una hoja del usuario. Aunque la heurística que usa el IDE puede tolerar incoherencias poco importantes en el diseño del archivo .vcxproj, se recomienda encarecidamente no desviarse de la estructura que se muestra anteriormente en este artículo.

## <a name="how-the-ide-uses-element-labels"></a>Cómo usa el IDE las etiquetas de elemento

En el IDE, al establecer la propiedad **UseOfAtl** en la página de propiedades general, se escribe en el grupo de propiedades de configuración del archivo de proyecto, mientras que la propiedad **TargetName** de la misma página de propiedades se escribe en el grupo de propiedades sin etiqueta de cada configuración. Visual Studio busca en el archivo .xml de la página de propiedades la información sobre dónde se escribe cada propiedad. Para la página de propiedades **General** (suponiendo que tenga una versión en inglés de Visual Studio Enterprise Edition), ese archivo es `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. En el archivo de reglas XML de página de propiedades se define la información estática sobre una regla y todas sus propiedades. Parte de esta información es la posición preferida de una propiedad de regla en el archivo de destino (es decir, el archivo donde se escribirá su valor). La posición preferida se especifica mediante el atributo Label de los elementos de archivo de proyecto.

## <a name="property-sheet-layout"></a>Diseño de la hoja de propiedades

El fragmento de código XML siguiente es un diseño mínimo de un archivo de hoja de propiedades (.props). Es similar a un archivo .vcxproj, y la funcionalidad de los elementos .props se puede deducir de la explicación anterior.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Para crear una hoja de propiedades propia, copie uno de los archivos .props de la carpeta VCTargets y modifíquelo para sus fines. Para Visual Studio 2017 Enterprise Edition, la ruta de acceso predeterminada de VCTargets es `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Vea también

[Trabajar con configuraciones de proyecto](working-with-project-properties.md)<br/>
[Archivos XML de página de propiedades](property-page-xml-files.md)
