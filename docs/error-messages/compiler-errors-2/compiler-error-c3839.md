---
title: Error del compilador C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754932"
---
# <a name="compiler-error-c3839"></a>Error del compilador C3839

no se puede cambiar la alineación en un tipo administrado o WinRT

La alineación de variables en tipos administrados o Windows Runtime se controla mediante CLR o Windows Runtime y no se puede modificar con [align](../../cpp/align-cpp.md).

El ejemplo siguiente genera el error C3839:

```cpp
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
