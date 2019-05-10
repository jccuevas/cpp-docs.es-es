---
title: Archivos XML de página de propiedades
ms.date: 05/06/2019
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 610dc7341a35845b35d8ed80f52b421d1c2fb5d1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217724"
---
# <a name="property-page-xml-rule-files"></a>Archivos XML de página de propiedades

Las páginas de propiedades de proyecto en el IDE se configuran mediante archivos XML en la carpeta VCTargets. La ruta de acceso exacta depende de qué ediciones de Visual Studio están instaladas y del idioma del producto. Para Visual Studio 2017 Enterprise Edition (en inglés) la ruta de acceso es `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Los archivos XML describen los nombres de las reglas, las categorías y las propiedades individuales, su tipo de datos, los valores predeterminados y cómo se van a mostrar. Cuando se establece una propiedad en el IDE, el valor nuevo se almacena en el archivo de proyecto.

Los únicos escenarios en los que es necesario comprender el funcionamiento interno de estos archivos y del IDE de Visual Studio son (a) cuando se quiere crear una página de propiedades personalizada, o bien (b) cuando se quieren personalizar las propiedades del proyecto de otra manera a través del IDE de Visual Studio.

En primer lugar, abra la página de propiedades de un proyecto (haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione Propiedades):

![Visual Studio C++ las propiedades del proyecto](../media/cpp-property-page-2017.png)

Cada nodo situado bajo **Propiedades de configuración** se denomina regla. En ocasiones, una regla representa una única herramienta como el compilador, pero en general, el término hace referencia a algo que tiene propiedades, que se ejecuta y que puede generar algún resultado. Cada regla se rellena a partir de un archivo XML en la carpeta VCTargets. Por ejemplo, la regla de C/C++ mostrada anteriormente se rellena desde "cl.xml".

Como se indicó anteriormente, cada regla tiene un conjunto de propiedades que se organizan en categorías. Cada subnodo de una regla representa una categoría. Por ejemplo, el nodo Optimización en C/C++ contiene todas las propiedades relacionadas con la optimización de la herramienta de compilador. Las propiedades y sus propios valores se representan en un formato de cuadrícula en el panel de la derecha.

Puede abrir cl.xml en el Bloc de notas o en cualquier editor XML (vea la captura de pantalla siguiente). Verá un nodo raíz denominado Regla que tiene la misma lista de propiedades definidas que las que se muestran en la interfaz de usuario, junto con metadatos adicionales.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
```

Hay un archivo XML correspondiente a cada nodo de Propiedades de configuración en la interfaz de usuario de páginas de propiedades. Puede agregar o quitar reglas en la interfaz de usuario mediante la inclusión o eliminación de las ubicaciones de los archivos XML correspondientes en el proyecto. Por ejemplo, así es cómo Microsoft.CppBuild.targets (un nivel por encima de la carpeta 1033) incluye cl.xml:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Si quita todos los datos de cl.xml, terminará con el esquema siguiente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

En la sección siguiente se describen todos los elementos principales y algunos de los metadatos que se les pueden adjuntar.

1. **Regla:**  Regla general es el nodo raíz en el archivo xml. puede tener muchos atributos:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   a. **Nombre:** El atributo Name es un identificador para la regla. Debe ser único entre todos los archivos XML de página de propiedades de un proyecto.

   b. **PageTemplate:** El valor de este atributo se utiliza la interfaz de usuario para elegir entre una colección de plantillas de la interfaz de usuario. La plantilla "tool" representa las propiedades en un formato de cuadrícula estándar. Otros valores integrados para este atributo son "debugger" y "generic". Vea el nodo Depuración y el nodo General, respectivamente, para ver el formato de la interfaz de usuario resultante de la especificación de estos valores. La interfaz de usuario para la plantilla de página "debugger" usa un cuadro de lista desplegable para cambiar entre las propiedades de otros depuradores, mientras que la plantilla "generic" muestra otras categorías de propiedades en la misma página en lugar de tener varios subnodos de categoría debajo del nodo Regla. Este atributo es solo una sugerencia para la interfaz de usuario; el archivo XML está diseñado para ser independiente de la interfaz de usuario. Es posible que en otra interfaz de usuario este atributo se use para otros fines.

   c. **SwitchPrefix:** Este es el prefijo que se usa en la línea de comandos de los modificadores. Un valor de "/" genera modificadores similares a /ZI, /nologo, /W3, etc.

   d. **Orden:** Se trata de una sugerencia para un posible cliente de la interfaz de usuario en la ubicación relativa de esta regla en comparación con todas las demás reglas en el sistema.

   e. **xmlns:** Se trata de un elemento XAML estándar. Puede ver tres espacios de nombres enumerados. Se corresponden con los espacios de nombres para las clases de deserialización XAML, el esquema XAML y el espacio de nombres del sistema, respectivamente.

   f. **DisplayName:** Este es el nombre que se muestra en la página de propiedades de la interfaz de usuario para el nodo de regla. Este valor se localiza. Se ha creado DisplayName como un elemento secundario de Regla en lugar de como un atributo (por ejemplo, Name o SwitchPrefix) debido a los requisitos de la herramienta de localización interna. Desde la perspectiva de XAML, ambos son equivalentes. Por tanto, se puede convertir simplemente en un atributo para reducir el desorden o dejarlo tal cual.

   g. **DataSource:** Se trata de una propiedad muy importante que le indica al sistema de proyecto la ubicación desde la que el valor de propiedad debe leen y escriben en y su agrupación (se explica más adelante). Para cl.xml, estos valores son los siguientes:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` indica al sistema del proyecto que todas las propiedades de Regla se deben escribir en el archivo de proyecto o el archivo de hoja de propiedades (en función del nodo que se haya usado para generar las páginas de propiedades). El otro valor posible es "UserFile", que escribirá el valor en el archivo .user.

   - `ItemType="ClCompile"` indica que las propiedades se almacenarán como metadatos de ItemDefinition o metadatos de elemento (este último solo si las páginas de propiedades se generaron desde un nodo de archivo en el Explorador de soluciones) de este tipo de elemento. Si no se establece este campo, la propiedad se escribe como una propiedad común en un PropertyGroup.

   - `Label=""` indica que cuando las propiedades se escriben como metadatos de `ItemDefinition`, la etiqueta del elemento primario ItemDefinitionGroup estará vacía (todos los elementos de MSBuild pueden tener una etiqueta). En Visual Studio 2017 se usan grupos con etiqueta para navegar por el archivo .vcxproj del proyecto. Tenga en cuenta que los grupos que contienen la mayoría de las propiedades de Regla tienen una cadena vacía como etiqueta.

   - `HasConfigurationCondition="true"` indica al sistema de proyecto que adjunte una condición de configuración al valor para que solo surta efecto para la configuración del proyecto actual (la condición se puede adjuntar al grupo primario o al propio valor). Por ejemplo, abra las páginas de propiedades del nodo de proyecto y establezca el valor de la propiedad **Tratar advertencias como errores** en **Propiedades de configuración > C/C++ > General** en "Sí". En el archivo del proyecto se escribe el valor siguiente. Observe la condición de configuración adjunta al elemento primario ItemDefinitionGroup.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Si este valor se estableciera en la página de propiedades de un archivo concreto, como stdafx.cpp, se escribiría bajo el elemento stdafx.cpp del archivo del proyecto, como se muestra a continuación. Observe cómo la condición de configuración se adjunta directamente a los propios metadatos.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Otro atributo de **DataSource** que no se muestra anteriormente es **PersistedName**. Puede usar este atributo para representar una propiedad en el archivo del proyecto mediante otro nombre. De forma predeterminada, este atributo se establece en el **Nombre** de la propiedad.

   Una propiedad individual puede invalidar el origen de datos de su elemento Regla primario. En ese caso, la ubicación para el valor de esa propiedad será diferente al de otras propiedades de la regla.

   h. Hay otros atributos de una regla como Description, SupportsFileBatching, etc., que no se muestran aquí. Para obtener el conjunto completo de los atributos aplicables a una regla o en cualquier otro elemento, examine la documentación para estos tipos. Como alternativa, puede examinar las propiedades públicas de los tipos en el espacio de nombres `Microsoft.Build.Framework.XamlTypes` del ensamblado `Microsoft.Build.Framework .dll`.

   i. **DisplayName**, **PageTemplate** y **Order** son propiedades relacionadas con la interfaz de usuario que están presentes en este modelo de datos que, en otros casos, es independiente de la interfaz de usuario. Con toda probabilidad estas propiedades se usarán en cualquier interfaz de usuario que se use para mostrar las páginas de propiedades. **DisplayName** y **Description** son dos propiedades que están presentes en casi todos los elementos del archivo XML. Y son las dos únicas que se localizan (la localización de estas cadenas se explicará en una publicación posterior).

1. **Categoría**: Una regla puede tener varias categorías. El orden en que se muestran las categorías en el archivo XML es una sugerencia para que la interfaz de usuario muestre las categorías en el mismo orden. Por ejemplo, el orden de las categorías en el nodo C/C++ como se vea en la interfaz de usuario (General, Optimización, Preprocesador, ...).  es el mismo que en cl.xml. Una categoría de ejemplo tiene el aspecto siguiente:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   En el fragmento de código anterior se muestran los atributos **Name** y **DisplayName** que se describieron antes. Una vez más, una propiedad **Category** puede tener otros atributos de los que se usan anteriormente. Puede obtener información sobre ellos si lee la documentación o examina los ensamblados mediante ildasm.exe.

1. **Propiedades:** Este es el grueso del archivo xml y contiene la lista de todas las propiedades de esta regla. Cada propiedad puede ser uno de los cinco tipos posibles que se muestran en el esqueleto de XAML anterior. Por supuesto, es posible que en el archivo solo tenga algunos de esos tipos. Una propiedad tiene un número de atributos que permiten que se pueda describir de manera enriquecida. Aquí solo se explicará **StringProperty**. El resto son muy similares.

    ```xml
    <StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
      <StringProperty.DisplayName>
        <sys:String>Object File Name</sys:String>
      </StringProperty.DisplayName>
      <StringProperty.Description>
        <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
      </StringProperty.Description>
    </StringProperty>
    ```

   La mayoría de los atributos del fragmento de código se han descrito antes. Los nuevos son Subtype, Category y Switch.

   a. **Subtype** es un atributo que solo está disponible para **StringProperty** y **StringListProperty**; proporciona información contextual. Por ejemplo, el valor de "file" indica que la propiedad representa una ruta de acceso de archivo. Esta información contextual se usa para mejorar la experiencia de edición proporcionando un Explorador de Windows como el editor de la propiedad que permite al usuario elegir el archivo de manera visual.

   b. **Categoría**: Esto declara que la categoría en la que pertenece esta propiedad. Intente buscar esta propiedad en la categoría **Archivos de salida** de la interfaz de usuario.

   c. **Conmutador:** Cuando una regla representa una herramienta – como la herramienta de compilador en este caso: mayoría de las propiedades de la regla se pasa como modificadores a la herramienta ejecutable durante el tiempo de compilación. El valor de este atributo indica el literal de modificador que se va a usar. La propiedad anterior especifica que su modificador debe ser **Fo**. Combinada con el atributo **SwitchPrefix** de la regla primaria, esta propiedad se pasa al archivo ejecutable como **/Fo"Debug\"** (visible en la línea de comandos de C/C++ en la interfaz de usuario de la página de propiedades).

   Otros atributos de propiedad incluyen los siguientes:

   d. **Visible:** Si por alguna razón, no desea que su propiedad se muestran en las páginas de propiedades (aunque probablemente todavía está disponible durante el tiempo de compilación), establezca este atributo en false.

   e. **ReadOnly:** Si desea proporcionar una vista de solo lectura del valor de esta propiedad en las páginas de propiedades, establezca este atributo en true.

   f. **IncludeInCommandLine:** Algunas propiedades no es posible que deba pasarse a una herramienta durante el tiempo de compilación. Si este atributo se establece en false, se impedirá que se pasen.
