---
title: Definir una Macro NMAKE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5997eee052ebba198e1fb52da35322c65a32627b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="defining-an-nmake-macro"></a>Definir una macro NMAKE
## <a name="syntax"></a>Sintaxis  
  
```  
  
macroname=string  
```  
  
## <a name="remarks"></a>Comentarios  
 El *Nombredelamacro* es una combinación de letras, dígitos y caracteres de subrayado (_) hasta 1.024 caracteres y distingue mayúsculas de minúsculas. El *Nombredelamacro* puede contener una macro invocada. Si *Nombredelamacro* consta únicamente de una macro, la macro que se va a invocar no puede ser null ni indefinido.  
  
 La `string` puede ser cualquier secuencia de cero o más caracteres. Una cadena nula contiene cero caracteres o solo espacios o tabulaciones. La `string` puede contener una llamada de macro.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Caracteres especiales en las macros](../build/special-characters-in-macros.md)  
  
 [Macros nulos y no definidas](../build/null-and-undefined-macros.md)  
  
 [Dónde definir macros](../build/where-to-define-macros.md)  
  
 [Prioridad en definiciones de macro](../build/precedence-in-macro-definitions.md)  
  
## <a name="see-also"></a>Vea también  
 [Macros y NMAKE](../build/macros-and-nmake.md)