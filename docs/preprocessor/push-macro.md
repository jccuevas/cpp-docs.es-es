---
title: push_macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6a389289f8849ac6155543299392586dcd389d2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078952"
---
# <a name="pushmacro"></a>push_macro
Guarda el valor de la *macro_name* macro en la parte superior de la pila para esta macro.

## <a name="syntax"></a>Sintaxis

```
#pragma push_macro("
macro_name
")
```

## <a name="remarks"></a>Comentarios

Puede recuperar el valor de *macro_name* con `pop_macro`.

Consulte [pop_macro](../preprocessor/pop-macro.md) para obtener un ejemplo.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)