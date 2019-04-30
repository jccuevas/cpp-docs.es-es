---
title: check_stack
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 49477a3b39db17047f349e341bd05c04954c964c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212404"
---
# <a name="checkstack"></a>check_stack
Indica al compilador que desactive la opción comprobaciones de la pila si `off` (o `-`) se especifica, o bien para activar los sondeos de pila si `on` (o `+`) se ha especificado.

## <a name="syntax"></a>Sintaxis

```
#pragma check_stack([ {on | off}] )
#pragma check_stack{+ | -}
```

## <a name="remarks"></a>Comentarios

Si no se especifica ningún argumento, las comprobaciones de la pila se tratan en la forma predeterminada. Esta pragma surte efecto en la primera función que se define después de que aparezca la pragma. Las comprobaciones de la pila no forman parte de las macros ni de las funciones insertadas que se generan.

Si no proporciona un argumento para el **check_stack** pragma, comprobación de pila revierte el comportamiento especificado en la línea de comandos. Para obtener más información, consulte [referencia del compilador](../build/reference/compiler-options.md). La interacción de la `#pragma check_stack` y [/Gs](../build/reference/gs-control-stack-checking-calls.md) opción se resume en la tabla siguiente.

### <a name="using-the-checkstack-pragma"></a>Utilización de la pragma check_stack

|Sintaxis|¿Se compila con<br /><br /> la opción /Gs?|Acción|
|------------|------------------------------------|------------|
|`#pragma check_stack( )`, o bien<br /><br /> `#pragma check_stack`|Sí|Desactiva la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack( )`, o bien<br /><br /> `#pragma check_stack`|No|Activa la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack(on)`<br /><br /> O `#pragma check_stack +`|Sí o no|Activa la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack(off)`<br /><br /> O `#pragma check_stack -`|Sí o no|Desactiva la comprobación de la pila para las funciones que la siguen|

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)