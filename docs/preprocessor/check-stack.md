---
title: check_stack (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 4c976692ec36cedcb73825ee0cc7093736a3a3dc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216127"
---
# <a name="check_stack-pragma"></a>check_stack (Pragma)

Indica al compilador que desactive las comprobaciones de la pila **-** si se especifica OFF (o), o para activar los sondeos de **+** la pila si se especifica **on** (o).

## <a name="syntax"></a>Sintaxis

> **#pragma check_stack (** [{ **on** | **OFF** }] **)** \
> **check_stack #pragma** { **+**  |  **-** }

## <a name="remarks"></a>Comentarios

Esta pragma surte efecto en la primera función que se define después de que aparezca la pragma. Las comprobaciones de la pila no forman parte de las macros ni de las funciones insertadas que se generan.

Si no proporciona un argumento para la pragma **check_stack** , la comprobación de la pila revierte al comportamiento especificado en la línea de comandos. Para obtener más información, vea [Opciones del compilador](../build/reference/compiler-options.md). La interacción de `#pragma check_stack` y la opción [/GS](../build/reference/gs-control-stack-checking-calls.md) se resume en la tabla siguiente.

### <a name="using-the-check_stack-pragma"></a>Utilización de la pragma check_stack

|Sintaxis|¿Se compila con<br /><br /> la opción /Gs?|.|
|------------|------------------------------------|------------|
|`#pragma check_stack( )`, o bien<br /><br /> `#pragma check_stack`|Sí|Desactiva la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack( )`, o bien<br /><br /> `#pragma check_stack`|Sin|Activa la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack(on)`<br /><br /> de`#pragma check_stack +`|Sí o no|Activa la comprobación de la pila para las funciones que la siguen|
|`#pragma check_stack(off)`<br /><br /> de`#pragma check_stack -`|Sí o no|Desactiva la comprobación de la pila para las funciones que la siguen|

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
