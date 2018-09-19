---
title: Error del compilador C3838 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3838
dev_langs:
- C++
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcf01ba87dc2e179e055417b6e2b78a90fd67cf5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064196"
---
# <a name="compiler-error-c3838"></a>Error del compilador C3838

no se puede heredar explícitamente de 'type'

Especificado `type` no puede actuar como clase base en cualquier clase.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3838:

```
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
