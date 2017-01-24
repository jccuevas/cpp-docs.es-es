---
title: "/Qfast_transcendentals (Force Fast Transcendentals) | Microsoft Docs"
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
  - "/Qfast_transcendentals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qfast_transcendentals"
  - "Force Fast Transcendentals"
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qfast_transcendentals (Force Fast Transcendentals)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera código insertado para las funciones transcendentales.  
  
## Sintaxis  
  
```  
/Qfast_transcendentals  
```  
  
## Comentarios  
 Esta opción del compilador fuerza a las funciones transcendentales a convertirse en código insertado para mejorar la velocidad de ejecución.  Esta opción sólo tiene efecto cuando se empareja con **\/fp:except** o **\/fp:precise**.  Generar código insertado para las funciones transcendentales es el comportamiento predeterminado bajo **\/fp:fast**.  
  
 Esta opción no es compatible con **\/fp:strict**.  Consulte [\/fp \(Especificar comportamiento de punto flotante\)](../../build/reference/fp-specify-floating-point-behavior.md) para obtener más información sobre las opciones del compilador de punto flotante.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)