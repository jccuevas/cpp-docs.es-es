---
title: Error del compilador C2307 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2307
dev_langs:
- C++
helpviewer_keywords:
- C2307
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7136b5b49371c9181780bfa4a7bc7a17416a7ad2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2307"></a>Error del compilador C2307
pragma 'pragma' debe estar fuera de la función si la compilación incremental está habilitada  
  
 Debe colocar el `data_seg` pragma entre funciones si está usando la compilación incremental.