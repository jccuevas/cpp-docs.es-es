---
title: Error del compilador C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176707"
---
# <a name="compiler-error-c3012"></a>Error del compilador C3012

> '*Intrinsic*': función intrínseca no permitida directamente dentro de una región paralela

Una función [intrínseca del compilador](../../intrinsics/compiler-intrinsics.md) no se permite en una región `omp parallel` . Para corregir este problema, mueva las funciones intrínsecas fuera de la región o reemplácelas con equivalentes no intrínsecos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3012 y se muestra una manera de corregirlo:

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
