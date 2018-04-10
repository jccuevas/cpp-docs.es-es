---
title: Cambios del sistema de compilación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.msbuild.changes
dev_langs:
- C++
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59d30e2afd07c21cb42dbc2b9109d7547d6c5b9f
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="build-system-changes"></a>Cambios del sistema de compilación
Se utiliza el sistema de MSBuild para compilar proyectos de Visual C++. Sin embargo, en Visual Studio 2008 y versiones anteriores, se utiliza el sistema de VCBuild. Ciertos tipos de archivo y conceptos que dependían de VCBuild no existe o se representan de forma diferente en el sistema actual. Este documento describen las diferencias en el sistema de compilación actual.  
  
## <a name="vcproj-is-now-vcxproj"></a>.vcproj es ahora .vcxproj  
 Archivos de proyecto ya no usan la extensión de nombre de archivo .vcproj. Visual Studio convierte automáticamente los archivos de proyecto creados por una versión anterior de Visual C++ para el formato utilizado por el sistema actual. Para obtener más información acerca de cómo actualizar manualmente un proyecto, vea [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).  
  
 En la versión actual, la extensión de nombre de archivo para un archivo de proyecto es. vcxproj.  
  
## <a name="vsprops-is-now-props"></a>.vsprops es ahora .props  
 En versiones anteriores, un *hoja de propiedades de proyecto* es un archivo basado en XML que tiene una extensión de nombre de archivo .vsprops. Una hoja de propiedades del proyecto le permite especificar modificadores para las herramientas de compilación, como el compilador o el vinculador y crear macros definidas por el usuario.  
  
 En la versión actual, la extensión de nombre de archivo para una hoja de propiedades de proyecto es. props.  
  
## <a name="custom-build-rules-and-rules-files"></a>Las reglas y los archivos .rules de compilación personalizada  
 En versiones anteriores, un *archivo de reglas* es un archivo basado en XML que tiene una extensión de nombre de archivo. Rules. Un archivo de reglas permite definir reglas de compilación personalizadas e incorporarlos al proceso de compilación de un proyecto de Visual C++. Una regla de compilación personalizada, que puede asociarse a una o más extensiones de nombre de archivo, le permite pasar archivos de entrada a una herramienta que crea uno o más archivos de salida.  
  
 En esta versión, las reglas de compilación personalizadas se representan mediante tres tipos de archivo, .xml, .props y .targets, en lugar de un archivo. Rules. Cuando se migra un archivo. Rules que se creó con una versión anterior de Visual C++ a la versión actual, se crean archivos .xml, .props y .targets equivalentes y se almacenan en el proyecto junto con el archivo .rules original.  
  
> [!IMPORTANT]
>  En la versión actual, la [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] no admite la creación de nuevas reglas. Por esta razón, la manera más fácil de usar un archivo de reglas de un proyecto que se creó con una versión anterior de Visual C++ es migrar el proyecto a la versión actual.  
  
## <a name="inheritance-macros"></a>Macros de herencia  
 En versiones anteriores, el **$ (Inherit)** macro especifica el orden en que aparecen las propiedades heredadas en la línea de comandos que está compuesta por el sistema de compilación del proyecto. El **$ (NoInherit)** macro hace que las incidencias de $ (Inherit) que se omitan y hace que las propiedades que harían en caso contrario, se heredan, no puede heredarse. Por ejemplo, de forma predeterminada la macro $ (Inherit) hace que los archivos que se especifica mediante la [/I (directorios de inclusión adicionales)](../build/reference/i-additional-include-directories.md) opción del compilador que se debe anexar a la línea de comandos.  
  
 En la versión actual, se admite la herencia especificando el valor de una propiedad como la concatenación de uno o más valores literales y macros de propiedad. El **$ (Inherit)** y **$ (NoInherit)** no admite las macros.  
  
 En el ejemplo siguiente, una lista delimitada por punto y coma se asigna a una propiedad en una página de propiedades. La lista se compone de la concatenación de la  *\<valor >* literal y el valor de la `MyProperty` propiedad, que se obtiene acceso mediante la notación de macro, **$(***MyProperty***)** .  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## <a name="vcxprojuser-files"></a>. vcxproj.user archivos  
 Un archivo de usuario (. vcxproj.user) almacena propiedades específicas del usuario, para la configuración de ejemplo, depuración e implementación. El archivo vcxproj.user se aplica a todos los proyectos para un usuario determinado.  
  
## <a name="vcxprojfilters-file"></a>.vcxproj.filters File  
 Cuando **el Explorador de soluciones** se utiliza para agregar un archivo a un proyecto, el archivo de filtros (. vcxproj.filters) define dónde en la **el Explorador de soluciones** vista se agrega el archivo, en función de su extensión de nombre de archivo de árbol.  
  
## <a name="vc-directories-settings"></a>Configuración de directorios de VC ++  
 Configuración de directorios de Visual C++ se especifica en el [página de propiedades de directorios de VC ++](../ide/vcpp-directories-property-page.md). En versiones anteriores de Visual Studio, la configuración de directorios aplica por usuario y la lista de directorios excluidos se especifica en el archivo sysincl.dat.  
  
 No se puede cambiar la configuración de directorios de VC ++ si ejecuta [/resetsettings devenv](/visualstudio/ide/reference/resetsettings-devenv-exe) en la línea de comandos. Tampoco puede cambiar la configuración si abre el **herramientas** menú, haga clic en **importar y exportar configuraciones**y, a continuación, seleccione la **restablecer todas las configuraciones** opción.  
  
 Migrar la configuración de directorios de VC ++ desde un archivo .vssettings creado por una versión anterior de Visual C++. Abra la **herramientas** menú, haga clic en **importar y exportar configuraciones**, seleccione **importar la configuración de entorno seleccionada**y, a continuación, siga las instrucciones del asistente. O cuando se inicia Visual Studio por primera vez, en la **elegir configuración de entorno predeterminada** cuadro de diálogo, seleccione **migrar mi configuración apta desde una versión anterior y aplicarla junto a la configuración predeterminada seleccionado debajo de**.  
  
## <a name="see-also"></a>Vea también  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)