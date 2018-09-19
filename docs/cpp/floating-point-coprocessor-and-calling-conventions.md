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
ms.openlocfilehash: e9f45f73e3cb1910bfc604c8a0fde871cef973a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075961"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesador de punto flotante y convenciones de llamada

Si está escribiendo ensamblado coprocesador de punto de rutinas para el flotante, se debe conservar flotante, seleccione la palabra de control y limpiar la pila del coprocesador a menos que se va a devolver un **float** o **doble** valor (que la función debe devolver en ST(0)).

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)