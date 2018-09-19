---
title: Sustitución de macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71ef2e1a8f337a4cd415169b6f9d817042f19a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894400"
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