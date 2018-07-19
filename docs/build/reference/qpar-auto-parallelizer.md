---
title: -/Qpar (Paralelizador automático) | Documentos de Microsoft
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
ms.openlocfilehash: 430bf1ebc79008d97435ecbcb3b15cf19dda5f8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375693"
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