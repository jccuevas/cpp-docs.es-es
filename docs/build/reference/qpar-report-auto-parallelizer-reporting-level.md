---
title: "-Qpar-report (nivel de información de Paralelizador automático) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70ae055d69341cc773b8b40ed1111b65ba5683cf
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (Nivel de información de paralelizador automático)
Habilita la característica de informes del compilador [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) y especifica el nivel de mensajes informativos de salida durante la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qpar-report:{1}{2}  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ Qpar-report: 1**  
 Genera un mensaje informativo para los bucles que se paralelizan.  
  
 **/ Qpar-report: 2**  
 Genera un mensaje informativo para los bucles que se paralelizan y también para los bucles que no se paralelizan, junto con un código de motivo.  
  
 Los mensajes se notifican a stdout. Si no se notifica ningún mensaje informativo, significa que el código no contiene bucles, o bien que el nivel de generación de informes no se estableció para notificar bucles no paralelizados. Para obtener más información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Cómo establecer la opción del compilador /Qpar-report en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** cuadro de diálogo **C/C++**, seleccione **línea de comandos**.  
  
3.  En el **opciones adicionales** cuadro, escriba `/Qpar-report:1` o `/Qpar-report:2`.  
  
### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Cómo establecer la opción del compilador /Qpar-report mediante programación  
  
-   Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/p/?linkid=263662)