---
title: Error del compilador C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 9f2c245e98609c8da8f5f89902d5c51bbf9d2b4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638677"
---
# <a name="compiler-error-c3222"></a>Error del compilador C3222

'parámetro': no se pueden declarar argumentos predeterminados para las funciones miembro de un tipo WinRT o administrado o funciones genéricas

No se permite declarar un parámetro de método con un argumento predeterminado. Para resolver el problema, puede usarse una forma sobrecargada del método. Es decir, defina un método con el mismo nombre pero sin parámetros y a continuación inicialice la variable en el cuerpo del método.

El código siguiente genera el error C3222: 

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
