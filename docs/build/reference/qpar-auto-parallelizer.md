---
title: -Qpar (Paralelizador automático) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c3501422a0bfbaba8aea0e45c102f63948b7db
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684510"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Paralelizador automático)
Habilita la [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) característica del compilador automáticamente paralelizar los bucles en el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el compilador paraleliza automáticamente bucles en el código, cálculo distribuye entre varios núcleos de procesador. Un bucle se paraleliza sólo si el compilador determina que es legal para hacerlo, y ese paralelización mejoraría el rendimiento.  
  
 El `#pragma loop()` directivas están disponibles para ayudar a que el optimizador de paralelizar los bucles específicos. Para obtener más información, consulte [bucle](../../preprocessor/loop.md).  
  
 Para obtener información acerca de cómo permitir que los mensajes de salida para el paralelizador automático, consulte [/qpar-Report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Qpar en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** cuadro de diálogo **C o C++**, seleccione **línea de comandos**.  
  
3.  En el **opciones adicionales** , escriba `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Para establecer la opción del compilador /Qpar mediante programación  
  
-   Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar-report (Paralelizador automático nivel)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Programación en paralelo en código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)