---
title: Error del compilador C2749 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2749
dev_langs:
- C++
helpviewer_keywords:
- C2749
ms.assetid: a81aef36-cdca-4d78-89d5-b72eff2500b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cccc06d9202297e1c86d87735621e12dd346cca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095227"
---
# <a name="compiler-error-c2749"></a>Error del compilador C2749

'type': solamente puede producir o detectar el identificador a una clase administrada con/CLR: safe

Cuando se usa **/CLR: safe**, solo se puede producir o detectar un tipo de referencia.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2749:

```
// C2749.cpp
// compile with: /clr:safe
ref struct MyStruct {
public:
   int i;
};

int main() {
   MyStruct ^x = gcnew MyStruct;

   // Delete the following 4 lines to resolve.
   try {
      throw (1);   // C2749
   }
   catch(int){}

   // OK
   try {
      throw (x);
   }
   catch(MyStruct ^){}
}
```