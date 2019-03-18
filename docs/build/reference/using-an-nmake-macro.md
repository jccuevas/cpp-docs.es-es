---
title: Utilizar una macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827424"
---
# <a name="using-an-nmake-macro"></a>Utilizar una macro NMAKE

Para utilizar una macro, escribir su nombre en paréntesis precedido por un signo de dólar ($) como sigue.

## <a name="syntax"></a>Sintaxis

```
$(macroname)
```

## <a name="remarks"></a>Comentarios

No se permiten espacios. Los paréntesis son opcionales si *Nombredelamacro* es un carácter individual. La cadena de definición reemplaza a $(*Nombredelamacro*); una macro no definida se reemplaza por una cadena nula.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Sustitución de macros](macro-substitution.md)

## <a name="see-also"></a>Vea también

[Macros y NMAKE](macros-and-nmake.md)
