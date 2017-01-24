---
title: "/Qvec-report (Nivel de informaci&#243;n de vectorizador autom&#225;tico) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qvec-report (Nivel de informaci&#243;n de vectorizador autom&#225;tico)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la característica de informe de errores del compilador [Auto\-Vectorizer](../../parallel/auto-parallelization-and-auto-vectorization.md) y especifica el nivel de mensajes informativos de salida durante la compilación.  
  
## Sintaxis  
  
```  
/Qvec-report:{1}{2}  
```  
  
## Comentarios  
 **\/Qvec\-report:1**  
 Genera un mensaje informativo para bucles que son vectorizados.  
  
 **\/Qvec\-report:2**  
 Genera un mensaje informativo para bucles que son vectorizados y bucles for que no son vectorizados, así como un código de error.  
  
 Para obtener información sobre los códigos de causa y mensajes, vea [Mensajes del vectorizador y paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### Para establecer la opción del compilador \/Qvec\-report en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo de **Páginas de propiedades** , en **C\/C\+\+**, seleccione **Línea de comandos**.  
  
3.  En el cuadro de **Opciones adicionales** , entre en `/Qvec-report: 1` o `/Qvec-report: 2`.  
  
### Para establecer la opción del compilador \/Qvec\-report mediante programación  
  
-   Utilice el ejemplo de código en <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/?LinkId=263662)