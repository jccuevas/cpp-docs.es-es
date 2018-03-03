---
title: Error del compilador C3661 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3661
dev_langs:
- C++
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea78138eb41d6e0db83d684dcfae1249a968945
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3661"></a>Error del compilador C3661
la lista de invalidación explícita no encontró ningún método para invalidar  
  
 Un reemplazo explícito especificaba uno o varios nombres de tipo.  Sin embargo, no había ninguna función con la firma necesaria en los tipos que coinciden con la firma de la función reemplazo.  Si intenta reemplazar basándose en el nombre de tipo, debe haber una o más funciones virtuales en el tipo especificado que coinciden con la firma de la función de reemplazo.  
  
 Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).