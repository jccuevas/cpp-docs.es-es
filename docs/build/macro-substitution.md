---
title: Sustitución de macros
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: d82aed5a34b7cafad0e40146470972dc6ff02424
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414686"
---
# <a name="macro-substitution"></a>Sustitución de macros

Cuando *Nombredelamacro* se invoca, cada aparición de *string1* en su definición de la cadena se reemplaza por *cadena2*.

## <a name="syntax"></a>Sintaxis

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Comentarios

Sustitución de macros distingue mayúsculas de minúsculas y es literal; *string1* y *cadena2* no se puede llamar a macros. Sustitución no modifica la definición original. Se puede sustituir el texto en cualquier macro predefinida excepto [ $$@ ](../build/filename-macros.md).

No hay espacios o tabulaciones preceden a los dos puntos; After los dos puntos se interpretan como literales. Si *cadena2* es null, todas las apariciones de *string1* se eliminan de la cadena de definición de la macro.

## <a name="see-also"></a>Vea también

[Uso de una macro NMAKE](../build/using-an-nmake-macro.md)
