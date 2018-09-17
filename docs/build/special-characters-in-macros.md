---
title: Caracteres especiales en las Macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a94001e2f912049518120911c25ae64afa24da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721434"
---
# <a name="special-characters-in-macros"></a>Caracteres especiales en las macros

Un signo de número (#) después de una definición especifica un comentario. Para especificar un signo de número literal en una macro, utilice un símbolo de intercalación (^), como en ^ #.

Un signo de dólar ($) especifica una llamada de macro. Para especificar un signo $ literal, utilice $$.

Para ampliar una definición de una nueva línea, al final de la línea con una barra diagonal inversa (\\). Cuando se invoca la macro, el carácter de barra diagonal inversa además de nueva línea se reemplaza por un espacio. Para especificar una barra diagonal inversa literal al final de la línea, precedidos por un símbolo de intercalación (^) o, seguido de un especificador de comentario (#).

Para especificar un carácter de nueva línea literal final de la línea con un símbolo de intercalación (^), como en:

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)