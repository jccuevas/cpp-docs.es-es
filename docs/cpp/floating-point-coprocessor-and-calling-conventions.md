---
title: Coprocesador de punto flotante y convenciones de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188629"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada

Si está escribiendo rutinas de ensamblado para el coprocesador de punto flotante, debe conservar la palabra de control de punto flotante y limpiar la pila del coprocesador a menos que esté devolviendo un valor **float** o **Double** (que la función debe devolver en St (0)).

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)
