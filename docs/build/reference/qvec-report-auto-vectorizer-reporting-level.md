---
title: -Qvec-report (Vectorizador automático nivel) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85f9d1c63f41b28982018bbe4507ff6bf87158fb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685858"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Nivel de información de vectorizador automático)
Habilita la característica informes del compilador [Vectorizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) y especifica el nivel de los mensajes informativos de salida durante la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ Qvec-report: 1**  
 Genera un mensaje informativo para los bucles que se ha vectorizado.  
  
 **/ Qvec-report: 2**  
 Genera un mensaje informativo para los bucles que se ha vectorizado y para los bucles que no vectorizados, junto con un código de motivo.  
  
 Para obtener información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Qvec-report en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** cuadro de diálogo **C o C++**, seleccione **línea de comandos**.  
  
3.  En el **opciones adicionales** , escriba `/Qvec-report:1` o `/Qvec-report:2`.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Para establecer la opción del compilador /Qvec-report mediante programación  
  
-   Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Programación en paralelo en código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)