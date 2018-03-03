---
title: Compilador advertencia (nivel 1) C4109 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4109
dev_langs:
- C++
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89966104dd6c6275c3bb364286915f414d692e23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4109"></a>Advertencia del compilador (nivel 1) C4109
identificador 'identifier' no esperado  
  
 La pragma que contiene el identificador no esperado se omite.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4109.cpp  
// compile with: /W1 /LD  
#pragma init_seg( abc ) // C4109  
```