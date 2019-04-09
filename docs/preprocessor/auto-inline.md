---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: c59dcc8ec7749a91565d5af043b1bd9e9eaa16ea
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033169"
---
# <a name="autoinline"></a>auto_inline
Excluye cualquier función definida dentro del intervalo donde **desactivar** se especifica a partir del que se consideran candidatas para la expansión automática alineada.

## <a name="syntax"></a>Sintaxis

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Comentarios

Para usar el **auto_inline** pragma, colóquela delante e inmediatamente después (no en) una definición de función. La pragma surte efecto en cuanto aparece en la primera definición de función.

## <a name="see-also"></a>Vea también

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)