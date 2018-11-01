---
title: Error de las herramientas del vinculador LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 7e95823e23215848ff3e5d201171523c9009eb2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571891"
---
# <a name="linker-tools-error-lnk2033"></a>Error de las herramientas del vinculador LNK2033

símbolo (token) de typeref sin resolver de 'type'

Un tipo no tiene una definición en metadatos MSIL.

Error LNK2033 puede producirse cuando se compila con **/CLR: safe** y donde hay solo una declaración adelantada para un tipo en un módulo MSIL, donde se hace referencia al tipo en el módulo MSIL.

El tipo debe definirse en **/CLR: safe**.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK2033.

```
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