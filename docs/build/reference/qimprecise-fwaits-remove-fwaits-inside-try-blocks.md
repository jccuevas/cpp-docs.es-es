---
title: -Qimprecise_fwaits (quitar comandos fwait en los bloques Try) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qimprecise_fwaits
dev_langs: C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aa09590e1ede80107a085c03528b4c9089885bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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