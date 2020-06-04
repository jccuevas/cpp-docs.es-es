---
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 5aef169c5632e74722438c63718ce5b783a8da09
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316608"
---
# <a name="alias"></a>ALIAS

La Directiva de **alias** crea un nombre alternativo para una función.  Esto le permite crear varios nombres para una función, o crear bibliotecas que permitan al vinculador (LINK. exe) asignar una función antigua a una nueva función.

## <a name="syntax"></a>Sintaxis

> Alias **\<** _alias_ **> = \<** _nombre real_ **>**

#### <a name="parameters"></a>Parameters

\ *de nombre real*
Nombre real de la función o el procedimiento.  Los corchetes angulares son obligatorios.

*alias*\
El nombre alternativo o de alias.  Los corchetes angulares son obligatorios.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
