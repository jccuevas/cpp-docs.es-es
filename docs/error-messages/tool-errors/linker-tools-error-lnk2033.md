---
title: Error de las LNK2033 las herramientas del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2033
dev_langs:
- C++
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6c547b4d35e2e7fe057cdd67f0dad47f58d000c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040002"
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