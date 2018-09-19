---
title: Error del compilador C3610 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037858"
---
# <a name="compiler-error-c3610"></a>Error del compilador C3610

'valuetype': tipo de valor debe ser 'boxing' antes de que se puede llamar el método 'método'

De forma predeterminada, un tipo de valor no está en el montón administrado. Antes de que se pueden llamar a métodos de las clases de .NET en tiempo de ejecución, como `Object`, tiene que mover el tipo de valor al montón administrado.

Solo es accesible a través de la opción del compilador obsoleto C3610 **/CLR: oldSyntax**.
