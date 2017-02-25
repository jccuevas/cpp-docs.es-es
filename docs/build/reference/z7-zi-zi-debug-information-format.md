---
title: "/Z7, /Zi, /ZI (Formato de la informaci&#243;n de depuraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.DebugInformationFormat"
  - "/zi"
  - "/z7"
  - "VC.Project.VCCLWCECompilerTool.DebugInformationFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C7 (opción del compilador compatible) [C++]"
  - "-Zl (opción del compilador) [C++]"
  - "formato de la información de depuración (opción del compilador)"
  - "ZI (opción del compilador)"
  - "-Zi (opción del compilador) [C++]"
  - "/ZI (opción del compilador) [C++]"
  - "Z7 (opción del compilador) [C++]"
  - "depurar [C++], archivos de información de depuración"
  - "Zi (opción del compilador) [C++]"
  - "none (opción del compilador) [C++]"
  - "/Zi (opción del compilador) [C++]"
  - "base de datos de programa (opción del compilador) [C++]"
  - "información de depuración simbólica completa"
  - "/Z7 (opción del compilador) [C++]"
  - "sólo números de línea (opción del compilador) [C++]"
  - "cl.exe (compilador), opciones de depuración"
  - "-Z7 (opción del compilador) [C++]"
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /Z7, /Zi, /ZI (Formato de la informaci&#243;n de depuraci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Seleccione el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto \(.obj\) o en una base de datos de programa \(PDB\).  
  
## Sintaxis  
  
```  
/Z{7|i|I}  
```  
  
## Comentarios  
 Estas opciones se describen en la siguiente tabla.  
  
 None  
 No se genera información de depuración, por lo que la compilación es más rápida.  
  
 **\/Z7**  
 Genera un archivo .obj que contiene información de depuración simbólica completa para usar con el depurador.  La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea.  No se genera ningún archivo .pdb.  
  
 Para distribuidores de bibliotecas de otros fabricantes, no tener un archivo .pdb supone una ventaja.  Sin embargo, los archivos .obj para los encabezados precompilados son necesarios durante la fase de vinculación y la depuración.  Si solo hay información de tipo \(y ningún código\) en los archivos de objeto .pch, también tendrá que compilar con [\/Yl \(Insertar referencia PCH para biblioteca de depuración\)](../../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
 **\/Zi**  
 Genera una base de datos de programa \(PDB\) que contiene información de tipos e información de depuración simbólica que se usa con el depurador.  La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea.  
  
 **\/Zi** no afecta a las optimizaciones.  Sin embargo, **\/Zi** sí implica **\/debug**; vea [\/DEBUG \(Generar información de depuración\)](../../build/reference/debug-generate-debug-info.md) para obtener más información.  
  
 La información de tipo se coloca en el archivo .pdb y no en el archivo .obj.  
  
 Puede utilizar [\/Gm \(Habilitar recompilación mínima\)](../../build/reference/gm-enable-minimal-rebuild.md) con **\/Zi**, mientras que **\/Gm** no está disponible al compilar con **\/Z7**.  
  
 Cuando se compila con **\/Zi** y **\/clr**, el atributo <xref:System.Diagnostics.DebuggableAttribute> no se coloca en los metadatos del ensamblado; deberá especificarlo en el código fuente, si lo desea.  Este atributo puede afectar al rendimiento de la aplicación en tiempo de ejecución.  Para obtener más información sobre cómo afecta al rendimiento el atributo Debuggable y cómo puede modificar el impacto en el rendimiento, vea [Facilitar la depuración de una imagen](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  
  
 **\/ZI**  
 Genera una base de datos de programa, como se describe anteriormente, con un formato compatible con la característica Editar y continuar.  Si desea usar la depuración con Editar y continuar, debe usar esta opción.  Dado que la mayoría de las optimizaciones son incompatibles con Editar y continuar, el uso de **\/ZI** deshabilita cualquier instrucción `#pragma optimize` del código.  
  
 **\/ZI** hace que se usen [\/Gy \(Habilitar vinculación en el nivel de función\)](../../build/reference/gy-enable-function-level-linking.md) y [\/FC \(Ruta de acceso completa de archivo de código fuente en diagnósticos\)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) en la compilación.  
  
 **\/ZI** no es compatible con [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  **\/ZI** solo está disponible en el compilador con destino en x86; esta opción del compilador no está disponible en los compiladores con destino en procesadores [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] o ARM.  
  
 El compilador asigna el nombre *project*.pdb a la base de datos de programa.  Si compila un archivo sin un proyecto, el compilador crea una base de datos denominada VC*x*0.pdb, donde *x* es la versión principal de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] en uso.  El compilador incrusta el nombre de la PDB en cada archivo .obj que crea con esta opción y hace apuntar el depurador a la ubicación de la información simbólica y de números de línea.  Si utiliza esta opción, los archivos .obj tendrán un tamaño menor, porque la información de depuración se almacena en el archivo .pdb y no en archivos .obj.  
  
 Si crea una biblioteca a partir de objetos compilados con esta opción, el archivo .pdb asociado debe estar disponible cuando se vincule la biblioteca a un programa.  Por lo tanto, si distribuye la biblioteca, debe distribuir el archivo PDB.  
  
 Para crear una biblioteca que contenga información de depuración sin utilizar archivos .pdb, debe seleccionar la opción del compilador Compatible con C 7.0 \(**\/Z7**\).  Si usa las opciones de encabezado precompilado, la información de depuración del encabezado precompilado y del resto del código fuente se incluye en el archivo PDB.  La opción **\/Yd** se pasa por alto cuando se especifica la opción Base de datos de programa.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Formato de la información de depuración**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)