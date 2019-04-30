---
title: Error del compilador C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: b8382213fbe7cc953dafd9610bfb993ba7837947
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400076"
---
# <a name="compiler-error-c3839"></a>Error del compilador C3839

no se puede cambiar la alineación en un tipo administrado o WinRT

Alineación de variables en administrados o tipos de Windows Runtime está controlada por el CLR o en tiempo de ejecución de Windows y no se puede modificar con [alinear](../../cpp/align-cpp.md).

El ejemplo siguiente genera el error C3839:

```
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