---
title: '-Zc: auto (deducir tipo de Variable) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd2f0ff353e1243685c94da0c28f29e810b2a9ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (Deducir tipo de variable)
El **/Zc: auto [-]** opción del compilador indica al compilador cómo usar el [palabra clave auto](../../cpp/auto-keyword.md) para declarar las variables. Si especifica la opción predeterminada, **/Zc: Auto**, el compilador deduce el tipo de la variable declarada a partir de su expresión de inicialización. Si especifica **/Zc:auto-**, el compilador asigna la variable a la clase de almacenamiento automático.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zc:auto[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 El estándar C++ define un significado original y uno revisado de la palabra clave `auto`. Antes de [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave declara una variable en la clase de almacenamiento automática; es decir, una variable que tiene una duración local. A partir de [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], la palabra clave deduce el tipo de una variable desde una expresión de inicialización de la declaración. Utilice la **/Zc: auto [-]** opción del compilador para indicar al compilador que use el significado original o modificado de la `auto` (palabra clave).  
  
 Si su forma de usar la palabra clave `auto` contradice la opción del compilador actual, el compilador emitirá el mensaje de diagnóstico correspondiente. Para obtener más información, consulte [palabra clave auto](../../cpp/auto-keyword.md). Para obtener más información acerca de los problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **propiedades de configuración** nodo.  
  
3.  Haga clic en el **C/C++** nodo.  
  
4.  Haga clic en el **línea de comandos** nodo.  
  
5.  Agregar **/Zc: Auto** o **/Zc:auto-** a la **opciones adicionales:** panel.  
  
## <a name="see-also"></a>Vea también  
 [/Zc (ajuste)](../../build/reference/zc-conformance.md)   
 [Auto (palabra clave)](../../cpp/auto-keyword.md)