---
title: "/GH (Habilitar la funci&#243;n de enlace _pexit) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_pexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh (opción del compilador) [C++]"
  - "_pexit (función)"
  - "Gh (opción del compilador) [C++]"
  - "-Gh (opción del compilador) [C++]"
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /GH (Habilitar la funci&#243;n de enlace _pexit)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama a la función `_pexit`  al final de cada método o función.  
  
## Sintaxis  
  
```  
/GH  
```  
  
## Comentarios  
 Dicha función no forma parte de ninguna biblioteca y se deja a criterio del programador proporcionar su definición.  
  
 Salvo que piense llamar de manera explícita a `_pexit`, no necesita proporcionar un prototipo.  La función debe parecer como si tuviera el siguiente prototipo, y debe insertar el contenido de todos los registros al entrar y extraer el contenido sin modificar al salir:  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit` es similar a `_penter`; puede ver un ejemplo de escritura de una función `_pexit` en [\/GH \(Habilitar la función de enlace \_penter\)](../../build/reference/gh-enable-penter-hook-function.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)