---
title: C2019 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2019
dev_langs: C++
helpviewer_keywords: C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf5c86bb837b89bd96e8e490e3668018affd6ca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2019"></a>C2019 de Error del compilador
se esperaba una directiva del preprocesador; se encontró 'carácter'  
  
 El carácter seguido de un `#` inicio de sesión, pero no es la primera letra de una directiva de preprocesador.  
  
 El ejemplo siguiente genera C2019:  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 Posible resolución:  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```