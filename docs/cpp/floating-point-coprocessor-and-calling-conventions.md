---
title: Coprocesador de punto flotante y convenciones de llamada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66ccd54c4abb1d8d9761d5ded88beba76bfae043
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401359"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada
Si está escribiendo ensamblado coprocesador de punto de rutinas para el flotante, se debe conservar flotante, seleccione la palabra de control y limpiar la pila del coprocesador a menos que se va a devolver un **float** o **doble** valor (que la función debe devolver en ST(0)).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)