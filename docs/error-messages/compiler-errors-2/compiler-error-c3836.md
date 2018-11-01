---
title: Error del compilador C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 33860273db07894a9a4d15ba6d578598a18819ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477550"
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
