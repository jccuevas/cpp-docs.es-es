---
title: Error del compilador C2978 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2978
dev_langs:
- C++
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40d7569a250812d6807c4723366b88e2f290be85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045190"
---
# <a name="compiler-error-c2978"></a>Error del compilador C2978

error de sintaxis: se esperaba 'palabraClave1' o 'palabraClave2'; se encontró el tipo 'palabraClave3'; no se admiten parámetros sin tipo en genéricos

Se declaró una clase genérica incorrectamente. Consulte [genéricos](../../windows/generics-cpp-component-extensions.md)para obtener más información.

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