---
title: Sustitución de macros
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: 43dc9133c53b1c436c0df8c3db66ae8f18604222
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321824"
---
# <a name="macro-substitution"></a>Sustitución de macros

Cuando *Nombredelamacro* se invoca, cada aparición de *string1* en su definición de la cadena se reemplaza por *cadena2*.

## <a name="syntax"></a>Sintaxis

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Comentarios

Sustitución de macros distingue mayúsculas de minúsculas y es literal; *string1* y *cadena2* no se puede llamar a macros. Sustitución no modifica la definición original. Se puede sustituir el texto en cualquier macro predefinida excepto [ $$@ ](filename-macros.md).

No hay espacios o tabulaciones preceden a los dos puntos; After los dos puntos se interpretan como literales. Si *cadena2* es null, todas las apariciones de *string1* se eliminan de la cadena de definición de la macro.

## <a name="see-also"></a>Vea también

[Uso de una macro NMAKE](using-an-nmake-macro.md)
