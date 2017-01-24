---
title: "/FA, /Fa (Archivo de lista) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.AssemblerListingLocation"
  - "VC.Project.VCCLCompilerTool.ConfigureASMListing"
  - "VC.Project.VCCLWCECompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.AssemblerListingLocation"
  - "/fa"
  - "VC.Project.VCCLCompilerTool.AssemblerOutput"
  - "VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FA (opción del compilador) [C++]"
  - "lista de sólo ensamblador"
  - "FA (opción del compilador) [C++]"
  - "-FA (opción del compilador) [C++]"
  - "mostrar lista de tipos de archivo"
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FA, /Fa (Archivo de lista)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un archivo de lista que contiene el código de ensamblado.  
  
## Sintaxis  
  
```  
/FA[c|s|u]  
/Fapathname  
```  
  
## Comentarios  
 Los argumentos controlan la generación de código fuente y de código máquina, así como la extensión del archivo de lista.  
  
 En la tabla siguiente, se describen los distintos valores para **\/FA**.  Es posible especificar más de un valor para **\/FA**.  Por ejemplo, se puede especificar **\/FAsu**.  
  
|Opción|Lista del contenido y extensión de archivo|  
|------------|------------------------------------------------|  
|**\/FA**|Código de ensamblado; .asm|  
|**\/FAc**|Código máquina y de ensamblado; .cod|  
|**\/FAs**|Código fuente y de ensamblado; .asm<br /><br /> Si se especifica **\/FAcs**, la extensión de archivo será .cod|  
|**\/FAu**|Hace que el archivo de salida se cree en formato UTF\-8, con un marcador de orden de bytes.  De forma predeterminada, la codificación de los archivos es ANSI, pero use **\/FAu** si desea un archivo de lista que se muestre correctamente en todos los sistemas, o si utiliza archivos de código fuente Unicode como entrada para el compilador.<br /><br /> Si se especifica **\/FAsu**, y si un archivo de código fuente utiliza codificación Unicode distinta de UTF\-8, las líneas de código del archivo .asm podrían no mostrarse correctamente.|  
  
 De forma predeterminada, el archivo de lista recibe el mismo nombre base que el archivo de código fuente.  Puede cambiar el nombre del archivo de lista y el directorio donde se crea por medio de la opción **\/Fa**.  
  
|Utilización de \/Fa|Resultado|  
|-------------------------|---------------|  
|**\/Fa**|Un *source\_file*.asm se crea para cada archivo de código fuente en la compilación.|  
|**\/Fa** *filename*|*filename*.asm se coloca en el directorio actual.  Sólo es válido al compilar un archivo de código fuente individual.|  
|**\/Fa** *filename.extension*|*filename.extension* se coloca en el directorio actual.  Sólo es válido al compilar un archivo de código fuente individual.|  
|**\/Fa** *directory*\\|Un *source\_file*.asm se crea y se coloca en *directory* especificado para cada archivo de código fuente en la compilación.  Observe la barra diagonal inversa requerida.  Sólo están permitidas las rutas de acceso del disco actual.|  
|**\/Fa** *directory*\\*filename*|*filename*.asm se coloca en `directory`especificado.  Sólo es válido al compilar un archivo de código fuente individual.|  
|**\/Fa** *directory*\\*filename.extension*|*filename.extension* se coloca en `directory`especificado.  Sólo es válido al compilar un archivo de código fuente individual.|  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Archivos de resultados**.  
  
4.  Modifique la propiedad **Ubicación de listas ASM** \(**\/Fa**\) o **Resultado del ensamblador** \(**\/FA**\) \(**\/FAu** se debe especificar en la página de propiedades **Línea de comandos**, en el cuadro **Opciones adicionales**\).  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> o <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>.  Para especificar **\/FAu**, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Ejemplo  
 La siguiente línea de comandos genera una combinación de lista de código fuente y código máquina denominada HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)