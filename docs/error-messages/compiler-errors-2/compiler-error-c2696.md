---
title: Error del compilador C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562881"
---
# <a name="compiler-error-c2696"></a>Error del compilador C2696

No se puede crear un objeto temporal de un tipo administrado 'type'

Las referencias a `const` en un programa no administrado que el compilador llame al constructor y cree un objeto temporal en la pila. Sin embargo, nunca puede crearse una clase administrada en la pila.

Solo es accesible a través de la opción del compilador obsoleto C2696 **/CLR: oldSyntax**.
