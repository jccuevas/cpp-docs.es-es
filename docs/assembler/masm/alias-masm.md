---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: ab00092f410d34119e876db4562e6d0709743d79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483504"
---
# <a name="alias-masm"></a>ALIAS (MASM)

El **ALIAS** directiva crea un nombre alternativo para una función.  Esto le permite crear varios nombres para una función o crear bibliotecas que permiten al vinculador (LINK.exe) para asignar una función antigua a una nueva función.

## <a name="syntax"></a>Sintaxis

> ALIAS \< *alias*> = \< *nombre real*>

#### <a name="parameters"></a>Parámetros

*nombre real*<br/>
El nombre real de la función o procedimiento.  Son necesarios los corchetes angulares.

*alias*<br/>
El nombre alternativo o alias.  Son necesarios los corchetes angulares.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>