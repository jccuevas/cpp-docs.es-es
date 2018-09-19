---
title: Del compilador (nivel 1) de la advertencia C4788 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8a6ad1aa3ae17944b8c2a292d484d55c24d9cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051742"
---
# <a name="compiler-warning-level-1-c4788"></a>Advertencia del compilador (nivel 1) C4788

'identificador': el identificador se ha truncado a 'número' caracteres

El compilador limita la longitud máxima permitida para un nombre de función. Cuando el compilador genera funclets para código EH/SEH, forma el nombre del funclet anteponiendo el nombre de función con algún texto, por ejemplo, "__catch," "\__unwind", u otra cadena.

El nombre del funclet resultante puede ser demasiado largo y el compilador lo truncará y generará la advertencia C4788.

Para resolver esta advertencia, acorte el nombre de función original. Si la función es un método o una función de plantilla de C++, utilice una definición de tipos para parte del nombre. Por ejemplo:

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

se puede reemplazar por:

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Esta advertencia sólo aparece en el x64 compilador.