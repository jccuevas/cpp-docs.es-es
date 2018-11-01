---
title: Cambios del sistema de compilación
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
ms.openlocfilehash: a7a98c864a1d0bf617ebf4ededea5e1a59a1af31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437159"
---
# <a name="build-system-changes"></a>Cambios del sistema de compilación

Se usa el sistema MSBuild para compilar proyectos de Visual C++. Sin embargo, en Visual Studio 2008 y versiones anteriores, se utiliza el sistema de VCBuild. Ciertos tipos de archivo y conceptos que dependían de VCBuild no existen o se representan de forma diferente en el sistema actual. Este documento describen las diferencias en el sistema de compilación actual.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj es ahora .vcxproj

Archivos de proyecto ya no usan la extensión de nombre de archivo .vcproj. Visual Studio convierte automáticamente los archivos de proyecto creados por una versión anterior de Visual C++ para el formato utilizado por el sistema actual. Para obtener más información acerca de cómo actualizar manualmente un proyecto, vea [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

En la versión actual, la extensión de nombre de archivo para un archivo de proyecto es. vcxproj.

## <a name="vsprops-is-now-props"></a>.vsprops es ahora .props

En versiones anteriores, un *hoja de propiedades del proyecto* es un archivo basado en XML que tiene una extensión de nombre de archivo vsprops. Una hoja de propiedades del proyecto le permite especificar los modificadores para las herramientas de compilación, como el compilador o vinculador y crear macros definidas por el usuario.

En la versión actual, la extensión de nombre de archivo para una hoja de propiedades del proyecto es. props.

## <a name="custom-build-rules-and-rules-files"></a>Archivos .rules y las reglas de compilación personalizada

En versiones anteriores, un *archivo reglas* es un archivo basado en XML que tiene una extensión de nombre de archivo. Rules. Un archivo de reglas le permite definir reglas de compilación personalizadas e incorporarlos en el proceso de compilación de un proyecto de Visual C++. Una regla de compilación personalizada, que puede asociarse con una o varias extensiones de nombre de archivo, le permite pasar archivos de entrada a una herramienta que crea uno o varios archivos de salida.

En esta versión, las reglas de compilación personalizada se representan mediante tres tipos de archivo, .xml, .props y .targets, en lugar de un archivo. Rules. Cuando un archivo .rules creado mediante el uso de una versión anterior de Visual C++ se migra a la versión actual, se crean archivos .xml, .props y .targets equivalentes y se almacenan en el proyecto junto con el archivo .rules original.

> [!IMPORTANT]
>  En la versión actual, el IDE no admite la creación de nuevas reglas. Por ese motivo, la manera más fácil de usar un archivo de reglas de un proyecto que se creó con una versión anterior de Visual C++ es migrar el proyecto a la versión actual.

## <a name="inheritance-macros"></a>Macros de herencia

En versiones anteriores, el **Inherit** macro especifica el orden en que aparecen las propiedades heredadas en la línea de comandos que está compuesta por el sistema de compilación del proyecto. El **NoInherit** macro hace que las apariciones de $ (Inherit) se pasará por alto y hace que cualquier las propiedades que normalmente se heredarían, no se puede heredar. Por ejemplo, de forma predeterminada la macro $ (Inherit) hace que los archivos especificados utilizando el [/I (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md) opción del compilador que se anexará a la línea de comandos.

En la versión actual, se admite la herencia especificando el valor de una propiedad como la concatenación de uno o más valores literales y macros de propiedades. El **Inherit** y **NoInherit** macros no se admiten.

En el ejemplo siguiente, una lista delimitada por punto y coma se asigna a una propiedad en una página de propiedades. La lista se compone de la concatenación de la  *\<valor >* literal y el valor de la `MyProperty` propiedad, que se accede mediante la notación de macro, **$(**  <em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. vcxproj.user archivos

Un archivo de usuario (. vcxproj.user) almacena propiedades específicas del usuario, para la configuración de ejemplo, depuración e implementación. El archivo vcxproj.user se aplica a todos los proyectos para un usuario determinado.

## <a name="vcxprojfilters-file"></a>. vcxproj.filters archivo

Cuando **el Explorador de soluciones** se usa para agregar un archivo a un proyecto, el archivo de filtros (. vcxproj.filters) define dónde en la **el Explorador de soluciones** vista se agrega el archivo, según su extensión de nombre de archivo de árbol.

## <a name="vc-directories-settings"></a>Configuración de directorios de VC ++

Configuración de directorios de Visual C++ se especifica en el [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md). En versiones anteriores de Visual Studio, la configuración de directorios aplica por usuario y la lista de directorios excluidos se especifica en el archivo sysincl.dat.

No se puede cambiar la configuración de directorios de VC ++ si ejecuta [/resetsettings devenv](/visualstudio/ide/reference/resetsettings-devenv-exe) en la línea de comandos. Tampoco puede cambiar la configuración si abre el **herramientas** menú, haga clic en **importar y exportar configuraciones**y, a continuación, seleccione el **restablecer todas las configuraciones** opción.

Migrar la configuración de directorios de VC ++ desde un archivo .vssettings que se crea mediante una versión anterior de Visual C++. Abra el **herramientas** menú, haga clic en **importar y exportar configuraciones**, seleccione **importar la configuración de entorno seleccionada**y, a continuación, siga las instrucciones del asistente. O cuando se inicia Visual Studio por primera vez, en el **Seleccionar configuración de entorno predeterminada** cuadro de diálogo, seleccione **migrar mi configuración apta desde una versión anterior y aplicarla además de la configuración predeterminada seleccionada a continuación**.

## <a name="see-also"></a>Vea también

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)