---
title: Error del compilador C2696 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e76b0c11d329c734b0609c540aca4315c7ed9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108747"
---
# <a name="compiler-error-c2696"></a>Error del compilador C2696

No se puede crear un objeto temporal de un tipo administrado 'type'

Las referencias a `const` en un programa no administrado que el compilador llame al constructor y cree un objeto temporal en la pila. Sin embargo, nunca puede crearse una clase administrada en la pila.

Solo es accesible a través de la opción del compilador obsoleto C2696 **/CLR: oldSyntax**.
