---
title: Error del compilador C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344604"
---
# <a name="compiler-error-c3610"></a>Error del compilador C3610

'valuetype': tipo de valor debe ser 'boxing' antes de que se puede llamar el método 'método'

De forma predeterminada, un tipo de valor no está en el montón administrado. Antes de que se pueden llamar a métodos de las clases de .NET en tiempo de ejecución, como `Object`, tiene que mover el tipo de valor al montón administrado.

Solo es accesible a través de la opción del compilador obsoleto C3610 **/CLR: oldSyntax**.
