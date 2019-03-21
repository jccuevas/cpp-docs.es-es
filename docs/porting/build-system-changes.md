---
title: Cambios en el sistema de compilación de Visual Studio 2010
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828181"
---
# <a name="build-system-changes"></a>Cambios del sistema de compilación

Para compilar proyectos de Visual C++, se usa el sistema MSBuild. Sin embargo, en Visual Studio 2008 y versiones anteriores, se utilizaba el sistema VCBuild. Ciertos conceptos y tipos de archivo que dependían de VCBuild no existen o se representan de forma distinta en el sistema actual. En este documento se describen las diferencias introducidas en el sistema de compilación actual.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj ahora es .vcxproj

Para los archivos de proyecto ya no se usa la extensión de nombre de archivo .vcproj. Visual Studio convierte automáticamente los archivos de proyecto creados por una versión anterior de Visual C++ al formato que se utiliza en el sistema actual. Para obtener más información sobre cómo actualizar manualmente un proyecto, vea [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

En la versión actual, la extensión de nombre de archivo de un archivo de proyecto es. vcxproj.

## <a name="vsprops-is-now-props"></a>.vsprops ahora es .props

En versiones anteriores, la *hoja de propiedades del proyecto* era un archivo basado en XML que tenía una extensión de nombre de archivo .vsprops. En la hoja de propiedades del proyecto se pueden especificar los modificadores para las herramientas de compilación, como el compilador o enlazador, y crear macros definidas por el usuario.

En la versión actual, la extensión de nombre de archivo de la hoja de propiedades de proyecto es .props.

## <a name="custom-build-rules-and-rules-files"></a>Reglas de compilación personalizada y archivos .rules

En versiones anteriores, un *archivo de reglas* era un archivo basado en XML que tenía una extensión de nombre de archivo .rules. Los archivos de reglas permiten definir reglas de compilación personalizada e incorporarlas en el proceso de compilación de un proyecto de Visual C++. Las reglas de compilación personalizada, que pueden asociarse con una o varias extensiones de nombre de archivo, permiten pasar archivos de entrada a una herramienta que crea uno o varios archivos de salida.

En esta versión, las reglas de compilación personalizada se representan mediante tres tipos de archivo (.xml, .props y .targets), en vez de hacerlo con un archivo .rules. Cuando un archivo .rules creado con una versión anterior de Visual C++ se migra a la versión actual, se crean los archivos .xml, .props y .targets equivalentes y se almacenan en el proyecto junto con el archivo .rules original.

> [!IMPORTANT]
>  En la versión actual, IDE no admite la creación de reglas nuevas. Por ese motivo, la forma más fácil de usar un archivo de reglas de un proyecto creado con una versión anterior de Visual C++ es migrar el proyecto a la versión actual.

## <a name="inheritance-macros"></a>Macros de herencia

En versiones anteriores, la macro **$(Inherit)** especifica el orden en que aparecen las propiedades heredadas en la línea de comandos compuesta por el sistema de compilación del proyecto. La macro **$(NoInherit)** hace que las apariciones de $(Inherit) se ignoren y que cualquier propiedad que en otras circunstancias se heredaría, no se pueda heredar. Por ejemplo, de forma predeterminada, la macro $(Inherit) hace que los archivos especificados utilizando la opción del compilador [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) se anexe a la línea de comandos.

En la versión actual, se admite la herencia mediante la especificación del valor de una propiedad como la concatenación de una o más macros de propiedades y valores literales. Las macros **$(Inherit)** y **$(NoInherit)** no se admiten.

En el ejemplo siguiente, se asigna una lista delimitada por punto y coma a una propiedad de la página de propiedades. La lista consiste en la concatenación del literal *\<value>* y del valor de la propiedad `MyProperty`, a la que se accede mediante la notación de macro **$(**<em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>Archivos . vcxproj.user

Los archivos de usuario (. vcxproj.user) almacenan propiedades específicas del usuario, como los valores de depuración e implementación. El archivo vcxproj.user se aplica a todos los proyectos de un usuario concreto.

## <a name="vcxprojfilters-file"></a>Archivo .vcxproj.filters

Cuando se usa el **Explorador de soluciones** para agregar un archivo a un proyecto, el archivo de filtros (.vcxproj.filters) define dónde se agrega el archivo en la vista de árbol del **Explorador de soluciones**, en función de su extensión de nombre de archivo.

## <a name="vc-directories-settings"></a>Configuración de directorios de Visual C++

La configuración de directorios de Visual C++ se especifican en la [página de propiedades de los directorios de Visual C++](../ide/vcpp-directories-property-page.md). En versiones anteriores de Visual Studio, la configuración de directorios se aplica por usuario y la lista de directorios excluidos se especifica en el archivo sysincl.dat.

No puede cambiar la configuración de los directorios de Visual C++ ejecutando [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) en la línea de comandos. Tampoco puede cambiarla si abre el menú **Herramientas**, hace clic en **Configuraciones de importación y exportación** y selecciona la opción **Restablecer todas las configuraciones**.

Migre la configuración de directorios de Visual C++ desde un archivo .vssettings creado mediante una versión anterior de Visual C++. Abra el menú **Herramientas**, haga clic en **Configuraciones de importación y exportación**, seleccione **Importar la configuración del entorno seleccionado** y siga las instrucciones del asistente. Otra opción es, al iniciar Visual Studio por primera vez, seleccionar**Migrar mi configuración apta desde una versión anterior y aplicarla junto a la configuración predeterminada seleccionada a continuación** en el cuadro de diálogo **Elegir configuración de entorno predeterminada**.

## <a name="see-also"></a>Vea también

[MSBuild on the Command Line - C++](../build/msbuild-visual-cpp.md) (MSBuild en la línea de comandos - C++)
