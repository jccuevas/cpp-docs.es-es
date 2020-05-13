---
title: ADVERTENCIA del compilador (nivel 1) C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: 99902edee371704c57a772e1b62f7ec4f41afb36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163694"
---
# <a name="compiler-warning-level-1-c4144"></a>ADVERTENCIA del compilador (nivel 1) C4144

' expresión ': expresión relacional como expresión switch

La expresión relacional especificada se usó como la expresión de control de una instrucción [Switch](../../cpp/switch-statement-cpp.md) . Se ofrecerán valores booleanos a las instrucciones Case asociadas. En el ejemplo siguiente se genera C4144:

```cpp
// C4144.cpp
// compile with: /W1
int main()
{
   int i = 0;
   switch(!i) {   // C4144, remove the ! to resolve
      case 1:
         break;
      default:
         break;
   }
}
```
