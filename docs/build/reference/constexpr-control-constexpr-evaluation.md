---
title: "-constexpr (Control constexpr de evaluación) | Documentos de Microsoft"
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /constexpr
- -constexpr
dev_langs:
- C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e594eb697c8972d28b513a3638d3eb704258b5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (control constexpr de evaluación)  
  
Use la **/constexpr** opciones del compilador para los parámetros de control para `constexpr` evaluación en tiempo de compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
> /constexpr:Depth*N*  
> /constexpr:backtrace*N*  
> /constexpr:Steps*N*  
  
## <a name="arguments"></a>Argumentos  
  
**profundidad***N*  
Limitar la profundidad de recursiva `constexpr` que la invocación de función *N* niveles. El valor predeterminado es 512.  
  
**seguimiento regresivo***N*  
Mostrar hasta *N* `constexpr` evaluaciones de diagnóstico. El valor predeterminado es 10.  
  
**pasos***N*  
Terminar `constexpr` evaluación después de *N* pasos. El valor predeterminado es 100.000.  
  
## <a name="remarks"></a>Comentarios  
  
El **/constexpr** opciones de compilador controlan la evaluación en tiempo de compilación de `constexpr` expresiones. Pasos de evaluación, los niveles de recursividad y seguimiento regresivo profundidad se controlan para impedir que el compilador pasan demasiado tiempo en `constexpr` evaluación. Para obtener más información sobre la `constexpr` elemento del lenguaje, consulte [constexpr (C++)](../../cpp/constexpr-cpp.md).  

El **/constexpr** opciones están disponibles a partir de Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.   
  
2. En **propiedades de configuración**, expanda la **C/C++** carpeta y elija el **línea de comandos** página de propiedades.  
  
3. Escriba cualquier **/constexpr** opciones del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
  
[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)