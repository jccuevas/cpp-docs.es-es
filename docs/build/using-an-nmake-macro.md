---
title: Utilizar una macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: a5f0fb9b13c5d5647b8f4ee382951df6282e8d68
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415648"
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

[Sustitución de macros](../build/macro-substitution.md)

## <a name="see-also"></a>Vea también

[Macros y NMAKE](../build/macros-and-nmake.md)
