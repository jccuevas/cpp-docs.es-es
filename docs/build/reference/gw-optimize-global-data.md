---
title: "/Gw (optimizar datos globales) | Microsoft Docs"
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
  - "/Gw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gw (opción del compilador) [C++]"
  - "-Gw (opción del compilador) [C++]"
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Gw (optimizar datos globales)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Empaquete los datos globales en las secciones COMDAT para la optimización.  
  
## Sintaxis  
  
```  
/Gw[-]  
```  
  
## Comentarios  
 La opción **\/Gw** hace que el compilador empaquete los datos globales en secciones individuales de COMDAT.  La opción **\/Gw** está desactivada de forma predeterminada y debe habilitarse explícitamente.  Para deshabilitarlo explícitamente, utilice **\/Gw\-**.  Cuando se habilitan **\/Gw** y [\/GL](../../build/reference/gl-whole-program-optimization.md), el vinculador utiliza la optimización de todo el programa con el fin de comparar las secciones COMDAT entre varios archivos objeto para excluir los datos globales sin referencia o para combinar los datos globales de solo lectura idénticos.  Esto puede reducir significativamente el tamaño del archivo ejecutable binario resultante.  
  
 Al compilar y vincular por separado, puede utilizar la opción del vinculador [\/OPT:REF](../../build/reference/opt-optimizations.md) para excluir del ejecutable los datos globales sin referencia en los archivos objeto compilados con la opción **\/Gw**.  
  
 También puede utilizar las opciones del vinculador [\/OPT:ICF](../../build/reference/opt-optimizations.md) y [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) juntas para combinar en el ejecutable los datos globales de solo lectura idénticos a través de varios archivos objeto compilados con la opción **\/Gw**.  
  
 Para obtener más información, vea la [introducción al modificador del compilador \/Gw](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) en el blog del equipo de Visual C\+\+.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir **\/Gw** y, a continuación, elija **Aceptar**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)