---
title: Compilador advertencia (nivel 1) C4081 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4081
dev_langs: C++
helpviewer_keywords: C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 228a279fa6d6b390a54b295586b57517e2f1a9bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4081"></a>Advertencia del compilador (nivel 1) C4081
se esperaba 'token1'; se encontró 'token2'  
  
 El compilador esperaba un token distinto en este contexto.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4081.cpp  
// compile with: /W1 /LD  
#pragma optimize) "l", on )   // C4081  
```