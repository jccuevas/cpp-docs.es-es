---
title: Compilador advertencia (nivel 1) C4440 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4440
dev_langs: C++
helpviewer_keywords: C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 418c49aa988c5cbf37b2307ca7f488dd9c4243d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4440"></a>Advertencia del compilador (nivel 1) C4440
llamar a la nueva definición de convención de 'convención_de_llamada1' a 'convención_de_llamada2'  
  
 Se omitió un intento para cambiar la convención de llamada.  
  
 El ejemplo siguiente genera C4440:  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```