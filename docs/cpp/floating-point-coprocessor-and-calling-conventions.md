---
title: Coprocesador de punto flotante y convenciones de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154248"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada

Si está escribiendo ensamblado coprocesador de punto de rutinas para el flotante, se debe conservar flotante, seleccione la palabra de control y limpiar la pila del coprocesador a menos que se va a devolver un **float** o **doble** valor (que la función debe devolver en ST(0)).

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)