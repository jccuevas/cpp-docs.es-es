---
title: Caracteres especiales en las Macros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c271d2f39a4d81776c06a107616170192e82d40d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="special-characters-in-macros"></a>Caracteres especiales en las macros
Un signo de número (#) después de una definición especifica un comentario. Para especificar un signo de número literal en una macro, utilice un símbolo de intercalación (^), como en ^ #.  
  
 Un signo de dólar ($) especifica una llamada de macro. Para especificar un signo $ literal, utilice $$.  
  
 Para ampliar una definición a una nueva línea, al final de la línea con una barra diagonal inversa (\\). Cuando se invoca la macro, el carácter de barra diagonal inversa además de nueva línea se reemplaza por un espacio. Para especificar una barra diagonal inversa literal al final de la línea, escríbalo con un símbolo de intercalación (^) o seguir con un especificador de comentario (#).  
  
 Para especificar un carácter de nueva línea literal final de la línea con un símbolo de intercalación (^), como en:  
  
```  
CMDS = cls^  
dir  
```  
  
## <a name="see-also"></a>Vea también  
 [Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)