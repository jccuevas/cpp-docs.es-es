---
title: auto_inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083183"
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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)