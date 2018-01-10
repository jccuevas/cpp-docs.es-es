---
title: -showIncludes (lista incluye archivos) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs: C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb88ff6d8a314ebd5cb0390f2c920f5b1d04e3e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="showincludes-list-include-files"></a>/showIncludes (Enumerar archivos de inclusión)
Hace que el compilador genere una lista de los archivos de inclusión. Anidar incluyen archivos son también mostrados (archivos que se incluyen en los archivos que incluyen).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/showIncludes  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando se encuentra un archivo de inclusión durante la compilación, un mensaje es la salida, por ejemplo:  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 Anidar incluyen archivos se indican mediante una sangría, un carácter de espacio para cada nivel de anidamiento, por ejemplo:  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 En este caso, `2.h` incluyó desde dentro de `1.h`, por lo tanto, la sangría.  
  
 El **/showIncludes** opción emite a `stderr`, no `stdout`.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **avanzadas** página de propiedades.  
  
4.  Modificar el **mostrar incluye** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)