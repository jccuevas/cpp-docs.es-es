---
title: VCBuild frente a MSBuild
description: El sistema de C++ compilación de Visual Studio cambió de VCBUILD a MSBuild en VIsual Studio 2010.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: ce3eb9e51a103aa54b74c7b5b4f775eb402269f1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076939"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild frente a MSBuild: cambios del sistema de compilación en Visual Studio 2010

El sistema MSBuild para C++ los proyectos se presentó en Visual Studio 2010. En Visual Studio 2008 y versiones anteriores, se usaba el sistema VCBuild. Ciertos tipos de archivo y conceptos que dependen de VCBuild no existen o se representan de forma diferente en MSBuild. En este documento se describen las diferencias introducidas en el sistema de compilación actual. Para convertir un proyecto de Visual Studio 2008 en MSBuild, debe usar Visual Studio 2010. Una vez convertido el proyecto, debe usar la versión más reciente de Visual Studio para actualizar al IDE actual y al conjunto de herramientas del compilador. Para obtener más información, incluido cómo obtener Visual Studio 2010, vea [instrucciones para visual studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

En las secciones siguientes se resumen los cambios de VCBuild a MSBuild. Si el proyecto de VCBUILD tiene reglas o macros de compilación personalizadas que MSBuild no reconoce, vea [proyectos de Visual C++ Studio:](../build/creating-and-managing-visual-cpp-projects.md) para obtener información sobre cómo traducir esas instrucciones al sistema MSBuild. La conversión inicial de VCBuild a MSBuild es simplemente un paso intermedio. No es necesario obtener el archivo de proyecto completamente correcto o para que el programa se compile sin errores. Solo se usa Visual Studio 2010 para convertir el proyecto al formato MSBuild para que el proyecto funcione en la versión más reciente de Visual Studio.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj ahora es .vcxproj

Para los archivos de proyecto ya no se usa la extensión de nombre de archivo .vcproj. Visual Studio 2010 convierte automáticamente los archivos de proyecto creados por una versión anterior de Visual C++ en el formato de MSBuild, que usa la extensión. vcxproj para los archivos de proyecto.

## <a name="vsprops-is-now-props"></a>.vsprops ahora es .props

En Visual Studio 2008 y versiones anteriores, una *hoja de propiedades de proyecto* es un archivo basado en XML que tiene una extensión de nombre de archivo. vsprops. En la hoja de propiedades del proyecto se pueden especificar los modificadores para las herramientas de compilación, como el compilador o enlazador, y crear macros definidas por el usuario. En MSBuild, la extensión de nombre de archivo de una hoja de propiedades de proyecto es. props.

## <a name="custom-build-rules-and-rules-files"></a>Reglas de compilación personalizadas y archivos. rules

En Visual Studio 2008 y versiones anteriores, un *archivo de reglas* es un archivo basado en XML que tiene una extensión de nombre de archivo. rules. Los archivos de reglas permiten definir reglas de compilación personalizada e incorporarlas en el proceso de compilación de un proyecto de Visual Studio C++. Las reglas de compilación personalizada, que pueden asociarse con una o varias extensiones de nombre de archivo, permiten pasar archivos de entrada a una herramienta que crea uno o varios archivos de salida.

En el sistema MSBuild, las reglas de compilación personalizadas se representan mediante tres tipos de archivo,. XML,. props y. targets, en lugar de un archivo. rules. Cuando un archivo. rules que se creó con una versión anterior de Visual C++ se migra a Visual Studio 2010, se crean archivos equivalentes. XML,. props y. targets y se almacenan en el proyecto junto con el archivo. rules original.

> [!IMPORTANT]
> En Visual Studio 2010, el IDE no admite la creación de nuevas reglas. Por ese motivo, la manera más sencilla de usar un archivo de reglas de un proyecto creado con una versión anterior de Visual C++ es migrar el proyecto a Visual Studio 2010.

## <a name="inheritance-macros"></a>Macros de herencia

En Visual Studio 2008 y versiones anteriores, la macro **$ (inherit)** especifica el orden en que aparecen las propiedades heredadas en la línea de comandos que se compone del sistema de compilación del proyecto. La macro **$(NoInherit)** hace que las apariciones de $(Inherit) se ignoren y que cualquier propiedad que en otras circunstancias se heredaría, no se pueda heredar. Por ejemplo, de forma predeterminada, la macro $(Inherit) hace que los archivos especificados utilizando la opción del compilador [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) se anexe a la línea de comandos.

En Visual Studio 2010, se admite la herencia especificando el valor de una propiedad como la concatenación de uno o más valores literales y macros de propiedad. Las macros **$(Inherit)** y **$(NoInherit)** no se admiten.

En el ejemplo siguiente, se asigna una lista delimitada por punto y coma a una propiedad de la página de propiedades. La lista consiste en la concatenación del literal *\<value>* y del valor de la propiedad `MyProperty`, a la que se accede mediante la notación de macro **$(** <em>MyProperty</em> **)** .

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>archivos. vcxproj. User

Los archivos de usuario (. vcxproj.user) almacenan propiedades específicas del usuario, como los valores de depuración e implementación. El archivo *vcxproj. User* se aplica a todos los proyectos de un usuario determinado.

## <a name="vcxprojfilters-file"></a>archivo. vcxproj. filters

Cuando se usa **Explorador de soluciones** para agregar un archivo a un proyecto, el archivo de filtros ( *. vcxproj. filters*) define dónde se agrega el archivo en la vista de árbol de **Explorador de soluciones** , en función de su extensión de nombre de archivo.

## <a name="vc-directories-settings"></a>Configuración de directorios de VC + +

La configuración de directorios de Visual C++ se especifican en la [página de propiedades de los directorios de Visual C++](../ide/vcpp-directories-property-page.md). En Visual Studio 2008 y versiones anteriores, la configuración de los directorios se aplica por usuario y la lista de directorios excluidos se especifica en el archivo *SYSINCL. dat* .

No puede cambiar la configuración de los directorios de Visual C++ ejecutando [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) en la línea de comandos. Tampoco puede cambiarla si abre el menú **Herramientas**, hace clic en **Configuraciones de importación y exportación** y selecciona la opción **Restablecer todas las configuraciones**.

Para migrar la configuración de los directorios de VC + + de un archivo *. vssettings* creado con una versión anterior de Visual Studio:

1. Abra el menú **herramientas** , haga clic en **importar y exportar configuraciones** .
2. Seleccione **importar la configuración de entorno seleccionada**
3. Siga las instrucciones del asistente.

## <a name="see-also"></a>Consulte también

[MSBuild on the Command Line - C++](../build/msbuild-visual-cpp.md) (MSBuild en la línea de comandos - C++)
