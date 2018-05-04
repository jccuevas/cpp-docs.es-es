---
title: -Od (deshabilitar (depurar)) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e287a9991f8192f16ec2f93e4068dc797ff72a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="od-disable-debug"></a>/Od (Deshabilitar (Depurar))
Desactiva todas las optimizaciones en el programa y acelera la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Od  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción es el valor predeterminado. Dado que **/Od** suprime el movimiento del código, simplifica el proceso de depuración. Para obtener más información acerca de las opciones de compilador para la depuración, vea [/Z7, / Zi, /ZI (formato de información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **optimización** página de propiedades.  
  
4.  Modificar el **optimización** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Z7, /Zi, /ZI (Formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md)