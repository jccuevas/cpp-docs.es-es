---
title: Error del compilador C3646 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3646
dev_langs:
- C++
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c038520c1a35fa5264e1e98b074687efb336d028
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "35658616"
---
# <a name="compiler-error-c3646"></a>Error del compilador C3646

> 'especificador': especificador de invalidación desconocido

## <a name="remarks"></a>Comentarios

El compilador encontró un token en la posición donde esperaba encontrar un especificador de invalidación, pero el compilador no reconoció el token.

Por ejemplo, si la no reconocido *especificador* es **_NOEXCEPT**, reemplácelo por la palabra clave **noexcept**.

Para obtener más información, consulte [especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3646 y muestra cómo corregirlo:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```