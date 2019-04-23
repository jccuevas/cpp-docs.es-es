---
title: Error del compilador C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: cf682bf14246754cca74a43dffc39761ff6125c1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779039"
---
# <a name="compiler-error-c2978"></a>Error del compilador C2978

error de sintaxis: se esperaba 'palabraClave1' o 'palabraClave2'; se encontró el tipo 'palabraClave3'; no se admiten parámetros sin tipo en genéricos

Se declaró una clase genérica incorrectamente. Consulte [genéricos](../../extensions/generics-cpp-component-extensions.md)para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2978.

```
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```