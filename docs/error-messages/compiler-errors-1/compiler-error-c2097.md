---
title: Error del compilador C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: cdb14aeef61d136a6992a05a72f382e589e88770
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207506"
---
# <a name="compiler-error-c2097"></a>Error del compilador C2097

inicialización no válida

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Inicialización de una variable con un valor no constante.

1. Inicialización de una dirección corta con una dirección larga.

1. Inicialización de una estructura, Unión o matriz local con una expresión no constante al compilar con **/za**.

1. Inicialización con una expresión que contiene un operador de coma.

1. Inicialización con una expresión que no es constante ni simbólica.
