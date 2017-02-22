---
title: "/Os, /Ot (Favorecer c&#243;digo peque&#241;o, favorecer c&#243;digo r&#225;pido) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed"
  - "/os"
  - "VC.Project.VCCLCompilerTool.FavorSizeOrSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Os (opción del compilador) [C++]"
  - "/Ot (opción del compilador) [C++]"
  - "código rápido"
  - "favorecer código rápido (opción del compilador) [C++]"
  - "favorecer código pequeño (opción del compilador) [C++]"
  - "Os (opción del compilador) [C++]"
  - "-Os (opción del compilador) [C++]"
  - "Ot (opción del compilador) [C++]"
  - "-Ot (opción del compilador) [C++]"
  - "código máquina pequeño"
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Os, /Ot (Favorecer c&#243;digo peque&#241;o, favorecer c&#243;digo r&#225;pido)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Minimiza o maximiza el tamaño de archivos EXE y DLL.  
  
## Sintaxis  
  
```  
/Os  
/Ot  
```  
  
## Comentarios  
 **\/Os** \(favorecer código pequeño\) reduce al mínimo el tamaño de los archivos ejecutables y DLL al ordenar al compilador que dé prioridad al tamaño sobre la velocidad.  El compilador puede reducir numerosas construcciones de C y C\+\+ a secuencias funcionalmente similares al código máquina.  En ocasiones, estas diferencias ofrecen contrapartidas de tamaño con respecto a la velocidad.  Las opciones **\/Os** y **\/Ot** permiten especificar la preferencia de una sobre la otra:  
  
 **\/Ot** \(favorecer código rápido\) eleva al máximo la velocidad de los archivos EXE y DLL, al ordenar al compilador que dé prioridad a la velocidad sobre el tamaño. Ésta es la opción predeterminada. El compilador puede reducir numerosas construcciones de C y C\+\+ a secuencias funcionalmente similares al código máquina.  En ocasiones, estas diferencias ofrecen contrapartidas de tamaño con respecto a la velocidad.  La opción \/Ot está implícita en la opción Maximizar velocidad \([\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)\).  La opción **\/O2** combina varias opciones para generar un código muy rápido.  
  
 Si utiliza **\/Os** o **\/Ot**, también debe especificar [\/Og](../../build/reference/og-global-optimizations.md) para optimizar el código.  
  
> [!NOTE]
>  La información que se recopila a partir de las series de pruebas de generación de perfiles reemplazará las optimizaciones que, en caso contrario, estarían activas si se especifica **\/Ob**, **\/Os** u **\/Ot**.  Para obtener más información, vea [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
 **Específico de x86**  
  
 El código del ejemplo siguiente muestra la diferencia entre las opciones Favorecer código pequeño \(**\/Os**\) y la opción Favorecer código rápido \(**\/Ot**\):  
  
> [!NOTE]
>  A continuación, se describe el comportamiento esperado al utilizar **\/Os** u **\/Ot**.  No obstante, el comportamiento del compilador puede variar de una versión a otra y producir diferentes optimizaciones del código.  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 Como se muestra en el fragmento de código del equipo inferior, si DIFFER.c se compila con prioridad del tamaño \(**\/Os**\), el compilador implementa la expresión de multiplicación en la instrucción return de forma explícita como una multiplicación para generar una secuencia de código corta, pero más lenta:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 Pero si DIFFER.c se compila con prioridad de la velocidad \(**\/Ot**\), el compilador implementa la expresión de multiplicación en la instrucción return como una serie de instrucciones shift y `LEA` para generar una secuencia de código rápida pero más larga:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **Específico de END x86**  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Tamaño o velocidad**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)