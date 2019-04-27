---
title: Instrucciones compuestas (Bloques)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 6aef2a0b5716ab501fabe80f0dda15080abe3ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154869"
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