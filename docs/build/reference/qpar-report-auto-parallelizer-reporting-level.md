---
title: "/Qpar-report (Nivel de informaci&#243;n de paralelizador autom&#225;tico) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Qpar-report (Nivel de informaci&#243;n de paralelizador autom&#225;tico)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la característica de informes [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) del compilador y especifica el nivel de los mensajes informativos de salida durante la compilación.  
  
## Sintaxis  
  
```  
/Qpar-report:{1}{2}  
```  
  
## Comentarios  
 **\/Qpar\-report:1**  
 Genera un mensaje informativo para los bucles que se paralelizan.  
  
 **\/Qpar\-report:2**  
 Genera un mensaje informativo para los bucles que se paralelizan y también para los bucles que no se paralelizan, junto con un código de motivo.  
  
 Los mensajes se notifican a stdout.  Si no se notifica ningún mensaje informativo, significa que el código no contiene bucles, o bien que el nivel de generación de informes no se estableció para notificar bucles no paralelizados.  Para obtener más información sobre los códigos de motivo y los mensajes, vea [Mensajes del vectorizador y paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### Cómo establecer la opción del compilador \/Qpar\-report en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, en **C\/C\+\+**, seleccione **Línea de comandos**.  
  
3.  En el cuadro **Opciones adicionales**, escriba `/Qpar-report:1` o `/Qpar-report:2`.  
  
### Cómo establecer la opción del compilador \/Qpar\-report mediante programación  
  
-   Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Programación en paralelo en código nativo](http://go.microsoft.com/fwlink/?LinkId=263662)