---
title: Advertencia del compilador C4687 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d813ce6d666431cfc3f74d1409012a4a0aec897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118718"
---
# <a name="compiler-warning-c4687"></a>Advertencia del compilador C4687

'class': una clase abstracta sellada no puede implementar una interfaz 'interface'

Normalmente, un tipo sealed abstracto sólo es útil para contener las funciones miembro estáticas.

Para obtener más información, consulte [abstracta](../../windows/abstract-cpp-component-extensions.md)y [sealed](../../windows/sealed-cpp-component-extensions.md).

C4687 se emite como un error de forma predeterminada. Puede suprimir C4687 con la [advertencia](../../preprocessor/warning.md) pragma. Si está seguro de que desea implementar una interfaz en un tipo sealed abstracto, puede suprimir la advertencia C4687.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4687.

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```