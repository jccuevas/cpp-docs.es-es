---
title: Error del compilador C3839 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 597d02ff347d399833e2376743b50f65e7674a18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092913"
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