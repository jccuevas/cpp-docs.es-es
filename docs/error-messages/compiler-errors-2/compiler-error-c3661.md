---
title: Error del compilador C3661 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3661
dev_langs:
- C++
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f290e5149000aa823da8c1e3ce1fabe533406de1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265313"
---
# <a name="compiler-error-c3661"></a>Error del compilador C3661
la lista de invalidación explícita no encontró ningún método para invalidar  
  
 Un reemplazo explícito especificaba uno o varios nombres de tipo.  Sin embargo, no había ninguna función con la firma necesaria en los tipos que coinciden con la firma de la función reemplazo.  Si intenta reemplazar basándose en el nombre de tipo, debe haber una o más funciones virtuales en el tipo especificado que coinciden con la firma de la función de reemplazo.  
  
 Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).