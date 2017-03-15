---
title: "/Wp64 (Detectar problemas de portabilidad de 64 bits) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems"
  - "VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems"
  - "/wp64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Wp64 (opción del compilador) [C++]"
  - "compilador de 64 bits [C++], detectar problemas de portabilidad"
  - "Wp64 (opción del compilador) [C++]"
  - "-Wp64 (opción del compilador) [C++]"
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# /Wp64 (Detectar problemas de portabilidad de 64 bits)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta opción del compilador está obsoleta. En versiones de Visual Studio anteriores a Visual Studio 2013, detecta problemas de portabilidad de 64 bits en tipos que también están marcados con la palabra clave [\_\_w64](../../cpp/w64.md).  
  
## Sintaxis  
  
```  
/Wp64  
```  
  
## Comentarios  
 De forma predeterminada, en las versiones de Visual Studio anteriores a Visual Studio 2013, la opción del compilador **\/Wp64** está desactivada en el compilador de Visual C\+\+ de 32 bits y en el compilador de Visual C\+\+ de 64 bits.  
  
> [!IMPORTANT]
>  La opción del compilador [\/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) y la palabra clave [\_\_w64](../../cpp/w64.md) está en desuso en Visual Studio 2010 y Visual Studio 2012 y no se admite a partir de Visual Studio 2013. Si convierte un proyecto que usa este modificador, el modificador no se migrará durante la conversión. Para usar esta opción en Visual Studio 2010 o Visual Studio 2012, debe escribir el modificador del compilador en **Opciones adicionales**, en la sección **Línea de comandos** de las propiedades del proyecto. Si usa la opción del compilador **\/Wp64** en la línea de comandos, el compilador emite la Advertencia de la línea de comandos D9002. En lugar de utilizar esta opción y la palabra clave para detectar problemas de portabilidad a 64 bits, use un compilador de Visual C\+\+ cuyo destino sea una plataforma de 64 bits y especifique la opción [\/W4](../../build/reference/compiler-option-warning-level.md). Para obtener más información, vea [Configurar programas de 64 bits](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
 Las variables de los tipos siguientes se comprueban en un sistema operativo de 32 bits como si se usaran en un sistema operativo de 64 bits:  
  
-   int  
  
-   long  
  
-   puntero  
  
 Si compila regularmente la aplicación utilizando un compilador de 64 bits, puede deshabilitar **\/Wp64** en las compilaciones de 32 bits porque el compilador de 64 bits detectará todos los problemas. Para obtener más información sobre cómo establecer como destino un sistema operativo Windows de 64 bits, consulte [Configurar programas de 64 bits](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  
  
     Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Modifique el cuadro **Opciones adicionales** para incluir **\/Wp64**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Configurar programas de 64 bits](../../build/configuring-programs-for-64-bit-visual-cpp.md)