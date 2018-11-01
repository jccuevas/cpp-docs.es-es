---
title: Error del compilador C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: ccbbb7875fdae48fd00f87f9a63f3764c143daae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442840"
---
# <a name="compiler-error-c2756"></a>Error del compilador C2756

'template type': no se permiten argumentos de plantilla predeterminados en una especialización parcial

La plantilla de una especialización parcial no puede contener un argumento predeterminado.

El siguiente ejemplo genera el error C2756 y muestra cómo corregirlo:

```
// C2756.cpp
template <class T>
struct S {};

template <class T=int>
// try the following line instead
// template <class T>
struct S<T*> {};   // C2756
```