---
title: -GX (habilitar el control de excepciones) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3013b4233621e63de0230e088dfc10ff65a5705d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="gx-enable-exception-handling"></a>/GX (Habilitar el control de excepciones)
Desusado. Habilita el control sincrónico de excepciones con la suposición de que las funciones declarado mediante `extern "C"` nunca producen una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GX  
```  
  
## <a name="remarks"></a>Comentarios  
 **/GX** está en desuso. Usar el equivalente [/EHsc](../../build/reference/eh-exception-handling-model.md) opción en su lugar. Para obtener una lista de opciones del compilador en desuso, consulte el **en desuso y quitar opciones de compilador** sección [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
 De forma predeterminada, **/EHsc**, el equivalente de **/GX**, está en vigor cuando se compila con el entorno de desarrollo de Visual Studio. Al usar las herramientas de línea de comandos, no se especifica ningún control de excepciones. Éste es el equivalente de **/GX-**.  
  
 Para obtener más información, consulte [control de excepciones de C++](../../cpp/cpp-exception-handling.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel de navegación, elija **propiedades de configuración**, **C/C++**, **línea de comandos**.  
  
3.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md)