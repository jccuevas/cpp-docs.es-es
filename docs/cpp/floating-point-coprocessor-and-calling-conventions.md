---
title: Coprocesador de punto flotante y convenciones de llamada | Documentos de Microsoft
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
ms.openlocfilehash: 46cf9c937453894ed37ad434ad94609d0744be24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410806"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada
Si está escribiendo ensamblado coprocesador de punto de rutinas para flotante, se debe conservar flotante palabra de control de punto y limpiar la pila del coprocesador a menos que va a devolver un **float** o **doble** valor (lo que la función debe devolver en ST(0)).  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)