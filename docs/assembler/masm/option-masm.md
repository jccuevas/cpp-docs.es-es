---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596487"
---
# <a name="option-masm"></a>OPTION (MASM)

Habilita y deshabilita las características del ensamblador.

## <a name="syntax"></a>Sintaxis

> OPCIÓN *ListaOpciones*

## <a name="remarks"></a>Comentarios

Las opciones disponibles incluyen:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULADOR**|
|**NOEMULATOR**|**EPÍLOGO**|**EXPR16**|**EXPR32**|
|**IDIOMA**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PRÓLOGO**|**READONLY**|**NOREADONLY**|
|**EL ÁMBITO**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

La sintaxis de LENGUAJE es **opción LANGUAGE:**<em>x</em>, donde *x* es uno de C, SYSCALL, STDCALL, PASCAL, FORTRAN o BASIC.  SYSCALL, PASCAL, FORTRAN y BASIC no se admiten con utilizado con [. MODELO](../../assembler/masm/dot-model.md) sin formato.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>