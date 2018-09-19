---
title: Error del compilador C2891 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d81662cb02fa3c8f6af75009daf4dab9b70196
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016564"
---
# <a name="compiler-error-c2891"></a>Error del compilador C2891

'parámetro': no se puede adquirir la dirección de un parámetro de plantilla

No se puede adquirir la dirección de un parámetro de plantilla a menos que sea un valor l. Parámetros de tipo no son valores l, ya que no hay ninguna dirección. Los valores sin tipo en listas de parámetros de plantilla que no son valores l no tienen también una dirección. Esto es un ejemplo de código que causa el Error del compilador C2891, porque el valor pasado como parámetro de plantilla es una copia generada por el compilador del argumento de plantilla.

```
template <int i> int* f() { return &i; }
```

Parámetros de plantilla que son valores l, tales como tipos de referencia, puede su dirección realizadas.

```
template <int& r> int* f() { return &r; }
```

Para corregir este error, no tomar la dirección de un parámetro de plantilla a menos que sea un valor l.