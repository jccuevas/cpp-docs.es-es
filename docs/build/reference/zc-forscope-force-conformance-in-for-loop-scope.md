---
title: "/Zc:forScope (Forzar ajuste en el &#225;mbito del bucle For) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope"
  - "VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope"
  - "/zc:forScope"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) [C++]"
  - "ajuste (opción del compilador)"
  - "Zc (opción del compilador) [C++]"
  - "-Zc (opción del compilador) [C++]"
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /Zc:forScope (Forzar ajuste en el &#225;mbito del bucle For)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se usa para implementar el comportamiento estándar de C\+\+ de los bucles [for](../../cpp/for-statement-cpp.md) con las extensiones de Microsoft \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\).  La opción **\/Zc:forScope** está activada de manera predeterminada.  
  
## Sintaxis  
  
```  
/Zc:forScope[-]  
```  
  
## Comentarios  
 La opción **\/Zc:forScope\-** está en desuso y se quitará en una próxima versión. El uso de **\/Zc:forScope\-** genera la advertencia de elemento en desuso D9035.  
  
 El comportamiento estándar consiste en dejar que el inicializador de un bucle **for** salga del ámbito después del bucle **for**. En **\/Zc:forScope\-** y [\/Ze](../../build/reference/za-ze-disable-language-extensions.md), el inicializador del bucle **for** permanece dentro del ámbito hasta que finaliza el ámbito local.  
  
 El siguiente código se compila en **\/Ze**, pero no en **\/Za**:  
  
```cpp  
// zc_forScope.cpp  
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp  
// C2065, D9035 expected  
int main() {  
    // Compile by using cl /Zc:forScope- zc_forScope.cpp  
    // to compile this non-standard code as-is.  
    // Uncomment the following line to resolve C2065 for /Za.  
    // int i;  
    for (int i = 0; i < 1; i++)  
        ;  
    i = 20;   // i has already gone out of scope under /Za  
}  
```  
  
 Si usa **\/Zc:forScope\-**, se generará una advertencia C4288 \(desactivada de forma predeterminada\) si una variable está dentro del ámbito debido a una declaración que se realizó en un ámbito anterior. Para mostrarlo, quite los caracteres `//` del código de ejemplo para declarar `int i`.  
  
 Puede modificar el comportamiento en tiempo de ejecución de **\/Zc:forScope** mediante la pragma [conform](../../preprocessor/conform.md).  
  
 Si usa **\/Zc:forScope\-** en un proyecto con un archivo .pch existente, se genera una advertencia, se ignora **\/Zc:forScope\-** y la compilación continúa con los archivos .pch existentes. Si quiere que se genere un nuevo archivo .pch, use [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md).  
  
 Para obtener más información sobre los problemas de conformidad de Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de navegación, abra **Propiedades de configuración**, **C o C\+\+**, página de propiedades de **Lenguaje**.  
  
3.  Modifique la propiedad **Forzar ajuste en el ámbito del bucle For**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)   
 [\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../../build/reference/za-ze-disable-language-extensions.md)