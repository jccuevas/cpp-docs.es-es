---
title: Coprocesador de punto flotante y convenciones de llamada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6d14f7f445064316c83b31e9b4cdc421d68d7255
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada
Si está escribiendo ensamblado coprocesador de punto de rutinas para flotante, se debe conservar flotante palabra de control de punto y limpiar la pila del coprocesador a menos que va a devolver un **float** o **doble** valor (lo que la función debe devolver en ST(0)).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)
