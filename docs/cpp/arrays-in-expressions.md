---
title: Matrices en expresiones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34f8a45dfa9de9a5a48e13cb6a38f667e5963f2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068551"
---
# <a name="arrays-in-expressions"></a>Matrices en expresiones

Cuando un identificador de un tipo de matriz aparece en una expresión distinta `sizeof`, dirección de (**&**), o la inicialización de una referencia, se convierte a un puntero al primer elemento de matriz. Por ejemplo:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

El puntero `psz` apunta al primer elemento de la matriz `szError1`. Tenga en cuenta que las matrices, a diferencia de los punteros, no son valores l modificables. Por consiguiente, la siguiente asignación no es válida:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Vea también

[Matrices](../cpp/arrays-cpp.md)