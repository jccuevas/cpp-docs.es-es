---
title: Instrucciones compuestas (bloques) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89e243dd1905e61a6c9a1b16c1936d7d6617ba17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116820"
---
# <a name="compound-statements-blocks"></a>Instrucciones compuestas (Bloques)

Una instrucción compuesta consta de cero o más instrucciones entre llaves (**{}**). Una instrucción compuesta se puede utilizar en cualquier lugar donde se espere una instrucción. Las instrucciones compuestas normalmente se denominan "bloques".

## <a name="syntax"></a>Sintaxis

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Comentarios

En el ejemplo siguiente se usa una instrucción compuesta como la *instrucción* forma parte de la **si** instrucción (consulte [if instrucción](../cpp/if-else-statement-cpp.md) para obtener más información sobre la sintaxis):

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
>  Dado que una declaración es una instrucción, una declaración puede ser una de las instrucciones en el *lista de instrucciones*. Por consiguiente, los nombres declarados dentro de una instrucción compuesta, pero no declarados explícitamente como static, tienen ámbito local y (para objetos) duración. Consulte [ámbito](../cpp/scope-visual-cpp.md) para obtener más información sobre el tratamiento de nombres con ámbito local.

## <a name="see-also"></a>Vea también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)