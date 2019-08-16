---
title: Error del compilador C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366373"
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