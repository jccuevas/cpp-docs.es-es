---
title: -Qimprecise_fwaits (quitar comandos fwait en los bloques Try) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a688f4b9f8f3c9302bb6a49e4b0a94a0e0931b33
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378059"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Quitar comandos fwait en los bloques Try)
Quita el `fwait` comandos internos de `try` se bloquea cuando se usa el [/fp: excepto](../../build/reference/fp-specify-floating-point-behavior.md) opción del compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Qimprecise_fwaits  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción no tiene ningún efecto si **/fp: excepto** también no se especifica. Si especifica la **/fp: excepto** opción, el compilador insertará un `fwait` comando alrededor de cada línea de código en un `try` bloque. De esta manera, el compilador puede identificar la línea de código que genera una excepción específica. **/ Qimprecise_fwaits** quita interno `fwait` instrucciones, dejando sólo las esperas alrededor de la `try` bloque. Esto mejora el rendimiento, pero solo se podrán realizar la extensión decir que el compilador `try` bloque produce una excepción, no la línea.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones /Q (operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)