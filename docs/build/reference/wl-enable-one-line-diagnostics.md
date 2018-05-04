---
title: -WL (habilitar diagnósticos de una línea) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58a6b41e66f7ec37ad02747edb8331049b9baef5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Habilitar diagnósticos de una línea)
Anexa información adicional a un mensaje de advertencia o error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/WL  
```  
  
## <a name="remarks"></a>Comentarios  
 Mensajes de error y advertencia del compilador de C++ pueden ir seguidos de información adicional que aparece de forma predeterminada, en una nueva línea. Cuando se compila desde la línea de comandos, se puede anexar a la línea de información adicional al mensaje de advertencia o error. Esto puede ser conveniente si se captura el resultado de la compilación en un archivo de registro y, a continuación, procesa dicho registro para buscar todos los errores y advertencias. Un punto y coma para separar el error o mensaje de advertencia de la línea adicional.  
  
 No todos los mensajes de advertencia y error tienen una línea de información adicional. El código siguiente generará un error que tiene una línea adicional de información; le permitirá comprobar el efecto cuando use **/WL**.  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
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