---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 274ac451005015b2693d8674673af574ec781bdc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399290"
---
# <a name="alias-masm"></a>ALIAS (MASM)

La Directiva de **alias** crea un nombre alternativo para una función.  Esto le permite crear varios nombres para una función, o crear bibliotecas que permitan al vinculador (LINK. exe) asignar una función antigua a una nueva función.

## <a name="syntax"></a>Sintaxis

> Alias **\<** _alias_ **> = \<** _nombre real_ **>**

#### <a name="parameters"></a>Parámetros

\ *de nombre real*
Nombre real de la función o el procedimiento.  Los corchetes angulares son obligatorios.

*alias*\
El nombre alternativo o de alias.  Los corchetes angulares son obligatorios.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
