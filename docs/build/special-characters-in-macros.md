---
title: Caracteres especiales en las Macros | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d954abc593fcba3887da4f7ee4bd5ce1e443e18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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