---
title: Archivos de regla de propiedad Page XML | Documentos de Microsoft
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
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b81e8965773c64144059fa433b54484c786159a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="property-page-xml-rule-files"></a>Archivos de regla de propiedad Page XML
Las páginas de propiedades de proyecto en el IDE se configuran por archivos XML en la carpeta VCTargets. La ruta de acceso exacta depende de qué ediciones de Visual Studio están instalados y el idioma del producto. Para Visual Studio de 2017 Enterprise Edition, en inglés, la ruta de acceso es `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Los archivos XML describen los nombres de las reglas, las categorías y las propiedades individuales, su tipo de datos, valores predeterminados y cómo se van a mostrar. Cuando se establece una propiedad en el IDE, el nuevo valor se almacena en el archivo de proyecto.

Los escenarios solo en el que necesita comprender el funcionamiento interno de estos archivos y el IDE de Visual Studio (a) que desea crear una página de propiedades personalizadas, o (b) que desee personalizar las propiedades del proyecto de alguna manera distinto a través del IDE de Visual Studio. 

En primer lugar, vamos a abrir las páginas de propiedades de un proyecto (haga clic con el botón secundario en el nodo de proyecto en **el Explorador de soluciones** y elija Propiedades):
   
![Propiedades de proyecto de Visual C++](media/cpp-property-page-2017.png)

Cada nodo en **propiedades de configuración** se denomina una regla. A veces, una regla representa una única herramienta como el compilador, pero en general, el término hace referencia a algo que tiene propiedades, que se ejecuta y que puede generar algún resultado. Cada regla se rellena a partir de un archivo xml en la carpeta VCTargets. Por ejemplo, la regla de C o C++ que se muestra anteriormente se rellena con 'cl.xml'.

Como se indicó anteriormente, cada regla tiene un conjunto de propiedades que se organizan en categorías. Cada nodo secundario en una regla representa una categoría. Por ejemplo, el nodo de optimización en C o C++ contiene todas las propiedades relacionadas con la optimización de la herramienta de compilador. Las propiedades y sus propios valores se representan en un formato de cuadrícula en el panel derecho.

Puede abrir cl.xml en el Bloc de notas o en cualquier editor de XML (vea a continuación de instantánea). Verá un nodo raíz denominado regla que tenga la misma lista de propiedades definidas en él, tal como se muestra en la interfaz de usuario, junto con los metadatos adicionales.

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

Hay un archivo XML correspondiente a cada nodo de propiedades de configuración en las páginas de propiedades de interfaz de usuario. Puede agregar o quitar las reglas en la interfaz de usuario mediante la inclusión o eliminación de ubicaciones de los archivos XML correspondientes en el proyecto. Por ejemplo, se trata cómo Microsoft.CppBuild.targets (un nivel por encima de la carpeta 1033) incluye cl.xml:

```xml  
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>

``` 
Si quitar cl.xml de todos los datos, terminará con el siguiente esquema:
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

La siguiente sección describe cada elementos principales y algunos de los metadatos que se pueden adjuntar a ellos.

1. **Regla:** regla general es el nodo raíz en el archivo xml, y puede tener muchos atributos:

```xml    
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```  

   a. **Nombre:** el atributo Name es un identificador para la regla. Debe ser único entre todos los archivos de xml de página Propiedades de un proyecto.

   b. **PageTemplate:** el valor de este atributo se utiliza la interfaz de usuario para elegir de una colección de plantillas de interfaz de usuario. La plantilla de "tool" presenta las propiedades en un formato de cuadrícula estándar. Otros valores integrado para este atributo son "depurador" y "genérico". Vea el nodo depuración y el nodo General, respectivamente, para ver el formato de la interfaz de usuario resultante de la especificación de estos valores. La interfaz de usuario para la plantilla de página "depurador" utiliza un cuadro de lista desplegable para cambiar entre las propiedades de depuradores diferentes, mientras que la plantilla "genérica" muestra las categorías de otro nombre de propiedad en una página en lugar de tener varios categoría subnodos debajo de la regla nodo. Este atributo es sólo una sugerencia para la interfaz de usuario; el archivo xml está diseñado para ser independiente de la interfaz de usuario. Una interfaz de usuario diferentes puede utilizar este atributo para propósitos diferentes.

  c. **SwitchPrefix:** este es el prefijo que se utilizará en la línea de comandos para los conmutadores. Un valor de "/" en los conmutadores que se parecen/Zi, / nologo, /W3, etcetera, se crearán.

  d. **Orden:** se trata de una sugerencia a un cliente potencial de interfaz de usuario en la ubicación relativa de esta regla en comparación con las demás reglas en el sistema.

  e. **xmlns:** se trata de un elemento XAML estándar. Puede ver tres espacios de nombres enumerados. Estos se corresponden con los espacios de nombres para la deserialización XAML clases, esquema y sistema de espacio de nombres XAML, respectivamente.

  f. **DisplayName:** éste es el nombre que se muestra en la página de propiedades de interfaz de usuario para el nodo de regla. Este valor se localiza. Hemos creado DisplayName como un elemento secundario de la regla en lugar de como un atributo (por ejemplo, nombre o SwitchPrefix) debido a la localización interno requisitos de la herramienta. Desde la perspectiva del XAML, ambos son equivalentes. Por lo tanto, puede simplemente hacer que un atributo que esté más despejado o dejarlo tal cual.

  g. **Origen de datos:** es una propiedad muy importante que le indica al sistema de proyecto la ubicación desde la que el valor de propiedad debe leer y escribir a y su agrupación (se explica más adelante). Para cl.xml, estos valores son:

```xml  
       <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
```  
   - `Persistence="ProjectFile`indica el sistema del proyecto que todas las propiedades de la regla deben escribirse en el archivo de proyecto o el archivo de hoja de propiedades (dependiendo de qué nodo se utilizó para generar las páginas de propiedades). El otro valor posible es "UserFile" que va a escribir el valor en el archivo .user.

   - `ItemType="ClCompile"`indica que las propiedades se almacenará como metadatos ItemDefinition o metadatos de elemento (éste último sólo si se han generado las páginas de propiedades de un nodo de archivo en el Explorador de soluciones) de este tipo de elemento. Si no se establece este campo, la propiedad se escribe como una propiedad común en un PropertyGroup.

   - `Label=""`indica que cuando las propiedades se escriben como `ItemDefinition` metadatos, la etiqueta del elemento primario ItemDefinitionGroup estará vacía (cada elemento de MSBuild puede tener una etiqueta). Visual Studio de 2017 usa grupos de etiquetado para navegar por el archivo .vcxproj del proyecto. Tenga en cuenta que los grupos que contienen la mayoría de las propiedades regla tienen una cadena vacía como una etiqueta.

   - `HasConfigurationCondition="true"`indica al sistema de proyecto para fijar una condición de configuración con el valor para que surte efecto sólo para la configuración del proyecto actual (la condición puede colocarse en el grupo primario o el propio valor). Por ejemplo, abra las páginas de propiedades del nodo de proyecto y establezca el valor de la propiedad **tratar advertencias como errores** en **propiedades de configuración > General de C o C++** en "Sí". El siguiente valor se escribe en el archivo de proyecto. Tenga en cuenta la condición de configuración adjunta al elemento primario ItemDefinitionGroup.

```xml  
     <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
           <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
     </ItemDefinitionGroup>
 ```
   Si este valor se establece en la página de propiedades de un archivo concreto, como stdafx.cpp, se escribiría el valor de propiedad en el elemento stdafx.cpp en el archivo de proyecto, tal y como se muestra a continuación. Observe cómo la condición de configuración está conectada directamente a los mismos metadatos.

 ```xml  
<ItemGroup>
   <ClCompile Include="stdafx.cpp">
      <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
   </ClCompile>
</ItemGroup>
 ```
   Otro atributo de **DataSource** no enumeradas anteriormente es **PersistedName**. Puede usar este atributo para representar una propiedad en el archivo de proyecto con un nombre diferente. De forma predeterminada, este atributo se establece en la propiedad **nombre**. 

   Una propiedad individual puede invalidar el origen de datos de su elemento primario regla. En ese caso, la ubicación para el valor de la propiedad será diferente de otras propiedades de la regla.

   h. Hay otros atributos de una regla como descripción, SupportsFileBatching, etcetera que no se muestran aquí. Al examinar la documentación para estos tipos, se puede obtener el conjunto completo de los atributos aplicables a una regla o en cualquier otro elemento. Como alternativa, puede examinar las propiedades públicas de los tipos del `Microsoft.Build.Framework.XamlTypes` espacio de nombres en la `Microsoft.Build.Framework .dll` ensamblado.

   i. **DisplayName**, **PageTemplate**, y **orden** están en caso contrario propiedades relacionadas con la interfaz de usuario que están presentes en este modelo de datos independiente de la interfaz de usuario. Estas propiedades son casi seguro que va a usar cualquier interfaz de usuario que se usa para mostrar las páginas de propiedades. **DisplayName** y **descripción** son dos propiedades que están presentes en casi todos los elementos en el archivo xml. Son las dos únicas propiedades que están localizadas (localización de estas cadenas se explicará en una publicación de una versión posterior).

2.  **Categoría:** una regla puede tener varias categorías. El orden en que las categorías se muestran en el archivo xml es una sugerencia para la interfaz de usuario para mostrar las categorías en el mismo orden. Por ejemplo, el orden de las categorías en el nodo C/C++ tal como se muestra en la interfaz de usuario: General, la optimización, el preprocesador,...  : es igual que en cl.xml. Una categoría de ejemplo tiene el siguiente aspecto:

```xml  
 <Category Name="Optimization">
    <Category.DisplayName>
        <sys:String>Optimization</sys:String>
    </Category.DisplayName>
 </Category>
```
Se muestra en el fragmento de código anterior la **nombre** y **DisplayName** atributos que se han descrito antes. Una vez más, hay otros atributos de un **categoría** puede tener que no se ha usado anteriormente. Puede saber acerca de ellos, lea la documentación o mediante el examen de los ensamblados utilizando ildasm.exe.

3. **Propiedades:** esto es el grueso del archivo xml y contiene la lista de todas las propiedades de esta regla. Cada propiedad puede ser uno de los cinco tipos posibles que se muestra en el esqueleto XAML anterior. Por supuesto, podría tener solo algunos de esos tipos en el archivo. Una propiedad tiene un número de atributos que permiten que se puede describir enriquecido. Explicamos solo la **StringProperty** aquí. El resto son muy similares.

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
La mayoría de los atributos en el fragmento de código se ha descrito antes. Los nuevos son subtipo, categoría y un conmutador.

   a. **Subtipo** está disponible solo para un atributo **StringProperty** y **StringListProperty**; proporciona información contextual. Por ejemplo, el valor de "file" indica que la propiedad representa una ruta de acceso de archivo. Dicha información contextual se utiliza para mejorar la experiencia de edición mediante el Explorador de Windows como el editor de la propiedad que permite al usuario elegir el archivo visualmente.

   b. **Categoría:** Esto declara la categoría en la que pertenece esta propiedad. Para buscar esta propiedad en el **archivos de salida** categoría en la interfaz de usuario.

   c. **Conmutador:** cuando una regla representa una herramienta, como la herramienta de compilador en este caso: mayoría de las propiedades de la regla se pasa como modificadores a la herramienta ejecutable durante el tiempo de compilación. El valor de este atributo indica el conmutador literal que se usará. La propiedad anterior especifica que debe ser su conmutador **Fo**. Combinar con la **SwitchPrefix** atributo en el elemento primario de regla, esta propiedad se pasa al archivo ejecutable como **/FO "depurar\"**  (visible en la línea de comandos de C o C++ en la página de propiedades de interfaz de usuario).

   Otros atributos de propiedad incluyen:

   d. **Visible:** si por alguna razón, no desea que aparezca en las páginas de propiedades (pero probablemente todavía está disponible durante el tiempo de compilación), establezca este atributo en false en la propiedad.

   e. **ReadOnly:** si desea proporcionar una vista de solo lectura del valor de esta propiedad en las páginas de propiedades, establezca este atributo en true.

   f. **IncludeInCommandLine:** algunas propiedades no es necesario que se pasa a una herramienta durante el tiempo de compilación. Si este atributo se establece en false impedirá se pasa.


