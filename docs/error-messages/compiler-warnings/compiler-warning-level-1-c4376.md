---
title: Advertencia del compilador (nivel 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: b1f6e7b403931f7fe1a67974ae85001cf80eab66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451602"
---
# <a name="compiler-warning-level-1-c4376"></a>Advertencia del compilador (nivel 1) C4376

el especificador de acceso 'especificador_antiguo:' ya no se admite: utilice 'especificador_nuevo:' en su lugar

Para obtener más información sobre cómo especificar la accesibilidad de los tipos y miembros en los metadatos, vea [escriba visibilidad](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [visibilidad de miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) en [Cómo: definir y utilizar clases y Structs (C++ / c++ / CLI) ](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4376.

```
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```