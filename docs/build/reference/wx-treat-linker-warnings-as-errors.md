---
title: "/WX (Tratar advertencias del vinculador como errores) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/WX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/WX (opción del vinculador)"
  - "WX (opción del vinculador)"
  - "-WX (opción del vinculador)"
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WX (Tratar advertencias del vinculador como errores)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/WX[:NO]  
```  
  
## Comentarios  
 \/WX hace que no se genere ningún archivo de salida si el vinculador genera una advertencia.  
  
 Esto es similar a **\/WX** para el compilador \(vea [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../../build/reference/compiler-option-warning-level.md) para más información\).  Sin embargo, la especificación de **\/WX** para la compilación no implica que **\/WX** también se aplique en la fase de vinculación; deberá especificar **\/WX** explícitamente para cada herramienta.  
  
 De forma predeterminada, **\/WX** se encuentra desactivado.  Para tratar las advertencias del vinculador como errores, especifique **\/WX**.  **\/WX:NO** equivale a no especificar **\/WX**.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)