---
title: Error del compilador C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386738"
---
# <a name="compiler-error-c3012"></a>Error del compilador C3012

> '*intrínseco*': función intrínseca no permitida directamente dentro de una región paralela

Una función [intrínseca del compilador](../../intrinsics/compiler-intrinsics.md) no se permite en una región `omp parallel` . Para corregir este problema, mueva intrínsecos fuera de la región, o reemplazarlos por sus equivalentes no intrínsecos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3012 y muestra una forma de corregirlo:

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```