---
title: "/Fp (Dar nombre al archivo .Pch) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderFile"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), asignar nombre"
  - "/Fp (opción del compilador) [C++]"
  - "Fp (opción del compilador) [C++]"
  - "-Fp (opción del compilador) [C++]"
  - "nombres [C++], PCH"
  - "asignar nombres a archivos de encabezado de precompilador"
  - "PCH (archivos), asignar nombre"
  - "archivos de encabezado precompilados, asignar nombre"
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fp (Dar nombre al archivo .Pch)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una ruta de acceso para un encabezado precompilado en lugar de utilizar la ruta de acceso predeterminada.  
  
## Sintaxis  
  
```  
/Fppathname  
```  
  
## Comentarios  
 Utilice esta opción con [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md) o [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md) para suministrar una ruta de acceso a un encabezado precompilado en lugar de usar la ruta predeterminada.  También puede usar **\/Fp** con **\/Yc** para que se utilice un archivo de encabezado precompilado diferente del indicado en el argumento `filename` de **\/Yc** y del nombre base del archivo de código fuente.  
  
 Si no especifica una extensión como parte de la ruta de acceso, se asume la extensión .pch.  Si especifica un directorio pero no especifica un nombre de archivo, el nombre de archivo predeterminado será VC`x`0.pch., donde `x` será la versión principal de Visual C\+\+ que se esté utilizando.  
  
 También puede utilizar la opción **\/Fp** con **\/Yu**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Encabezados precompilados**.  
  
4.  Modifique la propiedad **Archivo de encabezado precompilado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.  
  
## Ejemplo  
 Si desea crear un archivo de encabezado precompilado para una versión de depuración de un programa y compila tanto archivos de encabezado como de código fuente, puede especificar un comando como:  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## Ejemplo  
 El siguiente comando especifica el uso de un archivo de encabezado precompilado denominado MYPCH.pch.  El compilador supone que el código fuente de PROG.cpp se ha precompilado por medio de MYAPP.h y que ese código precompilado reside en MYPCH.pch.  Utiliza el contenido de MYPCH.pch y compila el resto de PROG.cpp para crear un archivo .obj.  El resultado de este ejemplo es un archivo denominado PROG.exe.  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)