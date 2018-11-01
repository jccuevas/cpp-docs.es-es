---
title: Error del compilador C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 17efd401314e93ff710be2c1e6f187a938e388b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648375"
---
# <a name="compiler-error-c3166"></a>Error del compilador C3166

'pointer': no se puede declarar un puntero a un puntero __gc interior como miembro de 'type'

El compilador encontró una declaración de puntero no válido (un `__nogc` puntero a un `__gc` puntero.).

Solo es accesible a través de la opción del compilador obsoleto C3166 **/CLR: oldSyntax**.
