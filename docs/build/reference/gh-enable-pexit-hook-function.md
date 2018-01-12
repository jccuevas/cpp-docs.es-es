---
title: "-GH (habilitar la función de enlace _pexit) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _pexit
dev_langs: C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02cfdd783a698a3397e84fa62b7252399570dc84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Habilitar la función de enlace _pexit)
Llamadas a la `_pexit` función al final de cada método o función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/GH  
```  
  
## <a name="remarks"></a>Comentarios  
 El `_pexit` función no forma parte de una biblioteca y depende de usted para proporcionar una definición para `_pexit`.  
  
 A menos que piense llamar explícitamente a `_pexit`, no es necesario proporcionar un prototipo. La función debe aparecer como si tuviera el siguiente prototipo, y se debe insertar el contenido de todos los registros de entrada y extraer el contenido sin modificar al salir:  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit`es similar a `_penter`; vea [/Gh (Enable _penter la función de enlace)](../../build/reference/gh-enable-penter-hook-function.md) para obtener un ejemplo de cómo escribir un `_pexit` función.  
  
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