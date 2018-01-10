---
title: "-homeparams (parámetros de registro de copia en la pila) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /homeparams
dev_langs: C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fff1b206620ef9efee3fc22c83c8d5317e99b607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Copiar los parámetros del Registro en la pila)
Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción del compilador sólo corresponde a los compiladores de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] (compilación nativa y cruzada).  
  
 Cuando se pasan parámetros en una [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] compilación, convenciones de llamada requieren espacio en la pila para los parámetros, incluso para los parámetros pasados en registros. Para obtener más información, consulte [pasando el parámetro](../../build/parameter-passing.md). Sin embargo, de forma predeterminada en una versión de lanzamiento, los parámetros de registro no se escribirán en la pila, en el espacio que se haya proporcionado para los parámetros. Esto dificulta la depuración de una generación optimizada (versión) del programa.  
  
 Para una versión de lanzamiento, use **/homeparams** para asegurarse de que puede depurar la aplicación. **/homeparams** implica una desventaja de rendimiento, ya que requiere un ciclo para cargar los parámetros de registro en la pila.  
  
 En una compilación de depuración, la pila siempre se rellena con parámetros pasados en registros.  
  
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