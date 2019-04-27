---
title: Error del compilador C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 17efd401314e93ff710be2c1e6f187a938e388b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174308"
---
# <a name="compiler-error-c3166"></a>Error del compilador C3166

'pointer': no se puede declarar un puntero a un puntero __gc interior como miembro de 'type'

El compilador encontró una declaración de puntero no válido (un `__nogc` puntero a un `__gc` puntero.).

Solo es accesible a través de la opción del compilador obsoleto C3166 **/CLR: oldSyntax**.
