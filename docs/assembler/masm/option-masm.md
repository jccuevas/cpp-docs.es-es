---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395165"
---
# <a name="option-masm"></a>OPTION (MASM)

Habilita y deshabilita las características del ensamblador.

## <a name="syntax"></a>Sintaxis

> **Opción** *optionlist*

## <a name="remarks"></a>Comentarios

Entre las opciones disponibles se incluyen:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULATOR**|
|**Noemulator**|**EPÍLOGO**|**EXPR16**|**EXPR32**|
|**MÓDULO**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**No(palabra clave)**|**NOSIGNEXTEND**|**POSICIÓN**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PRÓLOGO**|**READONLY**|**NOREADONLY**|
|**ÁMBITO**|**Sin ámbito**|**SEGMENT**|**SETIF2**.|

La sintaxis del lenguaje es **Option Language:** <em>x</em>, donde *x* es uno de C, syscall, Stdcall, Pascal, FORTRAN o Basic.  SYSCALL, PASCAL, FORTRAN y BASIC no se admiten con utilizado con [. ](../../assembler/masm/dot-model.md)plano de modelo.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
