---
title: Error del compilador C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676595"
---
# <a name="compiler-error-c2097"></a>Error del compilador C2097

inicialización no válida

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Inicialización de una variable con un valor no constante.

1. Inicialización de una dirección corta con una dirección larga.

1. Inicialización de un local estructura, unión o matriz con una expresión no constante cuando se compila con **/Za**.

1. Inicialización con una expresión que contenga un operador de comas.

1. Inicialización con una expresión que no es constante ni simbólica.