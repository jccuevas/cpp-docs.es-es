---
title: "/FU (Asignar nombre al archivo #using obligatorio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ForcedUsingFiles"
  - "/FU"
  - "VC.Project.VCNMakeTool.ForcedUsingAssemblies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FU (opción del compilador) [C++]"
  - "FU (opción del compilador) [C++]"
  - "-FU (opción del compilador) [C++]"
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FU (Asignar nombre al archivo #using obligatorio)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una opción del compilador que puede utilizar como alternativa a pasar un nombre de archivo a [\#using \(Directiva\)](../../preprocessor/hash-using-directive-cpp.md) en código fuente.  
  
## Sintaxis  
  
```  
/FU file  
```  
  
## Argumentos  
 `file`  
 Especifica el archivo de metadatos al que se hace referencia en esta compilación.  
  
## Comentarios  
 El modificador \/FU toma un único nombre de archivo.  Para especificar varios archivos, utilice \/FU con cada uno.  
  
 Si usa [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] y hace referencia a metadatos para utilizar la característica de [Ensamblados de confianza](../../dotnet/friend-assemblies-cpp.md) , no puede utilizar **\/FU**.  Debe hacer referencia a los metadatos en código mediante `#using`— junto con el atributo de `[as friend]` .  No se admiten los ensamblados de confianza en [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\).  
  
 Para obtener información sobre cómo crear un ensamblado o un módulo para Common Language Runtime \(CLR\), vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  Para obtener información sobre cómo compilar en [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)], vea [Compilar aplicaciones y bibliotecas](../Topic/Building%20apps%20and%20libraries%20\(C++-CX\).md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Forzar \#using**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)