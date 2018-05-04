---
title: -Ge (habilitar comprobaciones de la pila) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ge
dev_langs:
- C++
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce8b049426eb403e4bc41e842fe1ff2db1617dfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ge-enable-stack-probes"></a>/Ge (Habilitar comprobaciones de la pila)
Activa las comprobaciones de pila para cada llamada de función que requiere almacenamiento para las variables locales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Ge  
```  
  
## <a name="remarks"></a>Comentarios  
 Este mecanismo es útil si vuelve a escribir la funcionalidad de la comprobación de la pila. Se recomienda que use [/Gh (Enable _penter la función de enlace)](../../build/reference/gh-enable-penter-hook-function.md) en lugar de volver a escribir la comprobación de la pila.  
  
 [/GS (control Stack Checking Calls)](../../build/reference/gs-control-stack-checking-calls.md) tiene el mismo efecto.  
  
 **/GE** está en desuso; a partir de Visual Studio 2005, el compilador genera automáticamente la comprobación de pila. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y quitar opciones de compilador** en [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)