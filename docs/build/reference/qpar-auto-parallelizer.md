---
title: "-/Qpar (Paralelizador automático) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 073c906e7ecdfcf933e4b91cbcf8d6a77324df76
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Paralelizador automático)
Habilita la [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) característica del compilador automáticamente paralelizar bucles en el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el compilador ejecuta automáticamente paralelo bucles en el código, propaga de cálculo entre varios núcleos de procesador. Un bucle se paraleliza sólo si el compilador determina que es válido para hacerlo y que la ejecución en paralelo mejoraría el rendimiento.  
  
 El `#pragma loop()` directivas están disponibles para ayudar a que el optimizador paralelizar los bucles específicos. Para obtener más información, consulte [bucle](../../preprocessor/loop.md).  
  
 Para obtener información acerca de cómo habilitar los mensajes de salida para el paralelizador automático, consulte [/qpar-Report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Qpar en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** cuadro de diálogo **C/C++**, seleccione **línea de comandos**.  
  
3.  En el **opciones adicionales** cuadro, escriba `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Para establecer la opción del compilador /Qpar mediante programación  
  
-   Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar-informe (Paralelizador automático Reporting nivel)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/p/?linkid=263662)