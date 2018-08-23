---
title: -homeparams (copiar los parámetros de registro en la pila) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfd6b8c77d972eb4606e7095bc5f733e7db16ea6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42575519"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Copiar los parámetros del Registro en la pila)
Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción del compilador es solo para el x64 compiladores (compilación nativos y cruzada).  
  
 Cuando se pasan parámetros en un x64 compilación, las convenciones de llamada requieren espacio en la pila para los parámetros, incluso para los parámetros pasados en registros. Para obtener más información, consulte [pasando el parámetro](../../build/parameter-passing.md). Sin embargo, de forma predeterminada en una versión de lanzamiento, los parámetros de registro no se escribirán en la pila, en el espacio que se haya proporcionado para los parámetros. Esto dificulta la depuración de una generación optimizada (versión) del programa.  
  
 Para una versión de lanzamiento, utilice **/homeparams** para asegurarse de que puede depurar la aplicación. **/homeparams** implica una desventaja de rendimiento, ya que requiere un ciclo para cargar los parámetros de registro en la pila.  
  
 En una compilación de depuración, la pila siempre se rellena con los parámetros pasados en registros.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)