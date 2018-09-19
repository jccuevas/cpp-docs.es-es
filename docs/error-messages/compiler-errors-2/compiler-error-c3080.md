---
title: Error del compilador C3080 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3080
dev_langs:
- C++
helpviewer_keywords:
- C3080
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d56ad174d937598178a6eb203f8ca32361db67ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093642"
---
# <a name="compiler-error-c3080"></a>Error del compilador C3080

'función_finalizador': un finalizador no puede tener un especificador de clase de almacenamiento.

Para obtener más información, consulte [destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3080.

```
// C3080.cpp
// compile with: /clr /c
ref struct rs {
protected:
   static !rs(){}   // C3080
   !rs(){}   // OK
};
```