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
ms.openlocfilehash: cd0e5daa2232f17a34bee2f0d8b9569e524fbf34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189564"
---
# <a name="compound-statements-blocks"></a>Instrucciones compuestas (Bloques)

Una instrucción compuesta consta de cero o más instrucciones entre llaves ( **{}** ). Una instrucción compuesta se puede utilizar en cualquier lugar donde se espere una instrucción. Las instrucciones compuestas normalmente se denominan "bloques".

## <a name="syntax"></a>Sintaxis

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Observaciones

En el ejemplo siguiente se usa una instrucción compuesta como parte de la *instrucción* de la instrucción **If** (vea [la instrucción If](../cpp/if-else-statement-cpp.md) para obtener más información sobre la sintaxis):

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
>  Dado que una declaración es una instrucción, una declaración puede ser una de las instrucciones de la *lista de instrucciones*. Por consiguiente, los nombres declarados dentro de una instrucción compuesta, pero no declarados explícitamente como static, tienen ámbito local y (para objetos) duración. Vea [ámbito](../cpp/scope-visual-cpp.md) para obtener más información sobre el tratamiento de nombres con ámbito local.

## <a name="see-also"></a>Consulte también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)
