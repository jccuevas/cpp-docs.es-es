---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312955"
---
# <a name="macro"></a>MACRO

Marca un bloque de macro denominado *Name* y establece marcadores de posición de *parámetros* para los argumentos pasados cuando se llama a la macro.

## <a name="syntax"></a>Sintaxis

> *Name***macro** ⟦*parámetro* ⟦ **: REQ** | : =*valor predeterminado* | *args* **: vararg**⟧... ⟧\
> *instrucciones*\
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦ *⟧*

## <a name="remarks"></a>Notas

Una función de macro devuelve un *valor* a la instrucción de llamada.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Goto (MASM)](goto-masm.md)\
\ [ENDM](endm.md)
[Gramática BNF de MASM](masm-bnf-grammar.md)

