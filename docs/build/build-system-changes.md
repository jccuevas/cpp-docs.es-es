---
title: "Cambios del sistema de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.msbuild.changes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cambios del sistema de compilación, $(Inherit)"
  - "cambios del sistema de compilación, $(NoInherit)"
  - "cambios del sistema de compilación, .vsprops"
  - "cambios del sistema de compilación, reglas de compilación personalizadas"
  - "cambios del sistema de compilación, MSBuild"
  - "cambios del sistema de compilación, archivo del proyecto (.vcxprog)"
  - "MSBuild, cambios del sistema de compilación"
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Cambios del sistema de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se utiliza el sistema MSBuild para compilar los proyectos de Visual C\+\+.  Sin embargo, en Visual Studio 2008 y versiones anteriores, el sistema de VCBuild se utilizó.  Ciertos tipos de archivo y conceptos que dependieron de VCBuild no existen o se representan de manera diferente en el sistema actual.  En este documento se analizan las diferencias del sistema de compilación actual.  
  
## .vcproj es ahora .vcxproj  
 Los archivos de proyecto ya no usan la extensión de nombre de archivo .vcproj.  Visual Studio convierte automáticamente los archivos de proyecto creados en una versión anterior de Visual C\+\+ al formato que usa el sistema actual.  Para obtener más información sobre cómo actualizar manualmente un proyecto, vea [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md).  
  
 En la versión actual, la extensión de nombre de archivo de un archivo de proyecto es .vcxproj.  
  
## .vsprops es ahora .props  
 En versiones anteriores, una *hoja de propiedades del proyecto* es un archivo basado en XML que tiene una extensión de nombre de archivo .vsprops.  La hoja de propiedades del proyecto permite especificar modificadores para las herramientas de compilación, como el compilador o el vinculador, y crear macros definidas por el usuario.  
  
 En la versión actual, la extensión de nombre de archivo para una hoja de propiedades del proyecto es .props.  
  
## Reglas de compilación personalizadas y archivos .rules  
 En versiones anteriores, un *archivo de reglas* es un archivo basado en XML que tiene una extensión de nombre de archivo .rules.  El archivo de reglas permite definir reglas de compilación personalizadas e incorporarlas al proceso de compilación de un proyecto de Visual C\+\+.  Una regla de compilación personalizada, que se puede asociar a una o más extensiones de nombre de archivo, permite pasar archivos de entrada a una herramienta que crea uno o más archivos de salida.  
  
 En esta versión, las reglas de compilación personalizadas se representan mediante tres tipos de archivo, .xml, .props y .targets, en lugar de un archivo .rules.  Cuando un archivo .rules creado con una versión anterior de Visual C\+\+ se migra a la versión actual, se crean los archivos .xml, .props y .targets equivalentes y se almacenan en el proyecto junto con el archivo .rules original.  
  
> [!IMPORTANT]
>  En la versión actual, [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] no admite la creación de nuevas reglas.  Por esa razón, la manera más fácil de usar un archivo de reglas de un proyecto creado con una versión anterior de Visual C\+\+ es migrar el proyecto a la versión actual.  
  
## Macros de herencia  
 En versiones anteriores, la macro **$\(Inherit\)** especifica el orden en que las propiedades heredadas aparecen en la línea de comandos creada por el sistema de compilación del proyecto.  La macro **$\(NoInherit\)** hace que se omitan las apariciones de $\(Inherit\) y que no se herede ninguna propiedad que de otro modo se heredaría.  Por ejemplo, de forma predeterminada la macro $\(Inherit\) hace que los archivos especificados mediante la opción de compilador [\/I \(Directorios de inclusión adicionales\)](../build/reference/i-additional-include-directories.md) se anexen a la línea de comandos.  
  
 En la versión actual, la herencia se admite mediante la especificación del valor de una propiedad como la concatenación de uno o más valores literales y macros de propiedad.  No se admiten las macros **$\(Inherit\)** ni **$\(NoInherit\)**.  
  
 En el siguiente ejemplo, se asigna una lista delimitada por punto y coma a una propiedad de una página de propiedades.  La lista está formada por la concatenación de *\<value\>* literal y el valor de la propiedad de `MyProperty` , que se usa la notación de macro, **$\(***MyProperty***\)**.  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## Archivos .vcxproj.user  
 Un archivo de usuario \(.vcxproj .user\) almacena propiedades específicas del usuario, por ejemplo, parámetros de depuración e implementación.  El archivo vcxproj.user se aplica a todos los proyectos de un usuario determinado.  
  
## Archivo .vcxproj.filters  
 Cuando se usa el **Explorador de soluciones** para agregar un archivo a un proyecto, el archivo de filtros \(.vcxproj .filters\) define dónde se agrega el archivo en la vista de árbol del **Explorador de soluciones**, en función de su extensión de nombre de archivo.  
  
## Configuración de directorios de VC\+\+  
 La configuración de directorios de Visual C\+\+ se especifica en la [Directorios de VC\+\+ \(Página de propiedades\)](../ide/vcpp-directories-property-page.md).  En versiones anteriores de Visual Studio, la configuración de directorios se aplica por usuario y la lista de directorios excluidos se especifica en el archivo sysincl.dat.  
  
 No puede cambiar la configuración de directorios de VC\+\+ si ejecuta [devenv \/resetsettings](../Topic/-ResetSettings%20\(devenv.exe\).md) en la línea de comandos.  Tampoco puede cambiar la configuración si abre el menú **Herramientas**, hace clic en **Importar y exportar configuraciones** y, a continuación, selecciona la opción **Restablecer todas las configuraciones**.  
  
 La configuración de directorios de VC\+\+ se migra desde un archivo .vssettings creado por una versión anterior de Visual C\+\+.  Abra el menú **Herramientas**, haga clic en **Importar y exportar configuraciones**, seleccione **Importar la configuración de entorno seleccionada** y, a continuación, siga las indicaciones del asistente.  O bien, al iniciar Visual Studio por primera vez, en el cuadro de diálogo **Elegir configuración de entorno predeterminada**, seleccione **Migre mi configuración apta desde una versión anterior y aplicarla junto a la configuración predeterminada seleccionada a continuación**.  
  
## Vea también  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)