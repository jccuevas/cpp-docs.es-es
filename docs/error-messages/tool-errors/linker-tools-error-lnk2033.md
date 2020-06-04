---
title: Error de las herramientas del vinculador LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 407f5eaf94a0e2da43425c3bbdd1955a88c95f14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991175"
---
# <a name="linker-tools-error-lnk2033"></a>Error de las herramientas del vinculador LNK2033

token de TypeRef sin resolver (token) para ' tipo '

Un tipo no tiene una definición en los metadatos de MSIL.

LNK2033 puede producirse al compilar con **/clr: Safe** y donde solo hay una declaración adelantada para un tipo en un módulo MSIL, donde se hace referencia al tipo en el módulo MSIL.

El tipo debe definirse en **/clr: Safe**.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK2033.

```cpp
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```
