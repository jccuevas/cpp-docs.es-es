---
title: -C (conservar los comentarios durante el preprocesamiento) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs: C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d27e6ed0f6a2ff6e6f63bc1b87522fb598953c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conservar los comentarios durante el preprocesamiento)
Conserva los comentarios durante el preprocesamiento  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/C  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción del compilador requiere la **/E**, **/P**, o **/EP** opción.  
  
 El siguiente ejemplo de código mostrará el comentario de código de origen.  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 Este ejemplo genera el siguiente resultado.  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **preprocesador** página de propiedades.  
  
4.  Modificar el **mantener comentarios** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/E (Preprocesar para stdout)](../../build/reference/e-preprocess-to-stdout.md)   
 [/P (Preprocesar y escribir en un archivo)](../../build/reference/p-preprocess-to-a-file.md)   
 [/EP (Preprocesar para stdout sin directivas #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)