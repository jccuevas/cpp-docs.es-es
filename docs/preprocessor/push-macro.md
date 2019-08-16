---
title: push_macro
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
ms.openlocfilehash: 5602dd91b7d017c49a122524e469100b0ec6debf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179833"
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