---
title: Utilizar una Macro NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712600"
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