---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318753"
---
# <a name="option"></a>OPTION

Habilita y deshabilita las características del ensamblador.

## <a name="syntax"></a>Sintaxis

> **Opción** *optionlist*

## <a name="remarks"></a>Notas

Entre las opciones disponibles se incluyen:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULATOR**|
|**Noemulator**|**EPÍLOGO**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**No(palabra clave)**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PRÓLOGO**|**READONLY**|**NOREADONLY**|
|**ÁMBITO**|**Sin ámbito**|**SEGMENT**|**SETIF2**.|

La sintaxis del lenguaje es **Option Language:** <em>x</em>, donde *x* es uno de C, syscall, Stdcall, Pascal, FORTRAN o Basic.  SYSCALL, PASCAL, FORTRAN y BASIC no se admiten con [. ](dot-model.md)plano de modelo.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
