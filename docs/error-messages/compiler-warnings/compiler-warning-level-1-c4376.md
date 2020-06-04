---
title: Advertencia del compilador (nivel 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 8009d2e5d09ad173f6150ebe9a907be9f4947cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162861"
---
# <a name="compiler-warning-level-1-c4376"></a>Advertencia del compilador (nivel 1) C4376

el especificador de acceso 'especificador_antiguo:' ya no se admite: utilice 'especificador_nuevo:' en su lugar

Para obtener más información sobre cómo especificar la accesibilidad de tipos y miembros en los metadatos, vea [visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [visibilidad de miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) en [Cómo: definir yC++utilizar clases y Structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4376.

```cpp
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
