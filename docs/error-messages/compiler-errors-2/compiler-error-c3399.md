---
title: Error del compilador C3399 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3399
dev_langs:
- C++
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3cae3c038e4af4a58756ad7387472c081bf4c3d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016798"
---
# <a name="compiler-error-c3399"></a>Error del compilador C3399

'tipo': no se pueden proporcionar argumentos cuando se crea una instancia de un parámetro genérico

Cuando se especifica la restricción `gcnew()` , se indica que el tipo de restricción tendrá un constructor sin parámetros. Por lo tanto, es un error tratar de crear una instancia de ese tipo y pasar un parámetro.

Consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3399.

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```