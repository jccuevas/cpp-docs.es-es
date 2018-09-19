---
title: Error del compilador C3836 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3836
dev_langs:
- C++
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1349ff88c00f8091a8187bb963f4fb683b694e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046035"
---
# <a name="compiler-error-c3836"></a>Error del compilador C3836

constructor estático no puede tener una lista de inicializadores de miembro

Una clase administrada no puede tener un constructor estático que también tiene una lista de inicialización de miembro. Constructores de clase estática son llamados por common language runtime para la inicialización, inicializar a miembros de datos estáticos de clase.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3836:

```
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
