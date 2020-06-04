---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076149"
---
# <a name="macro"></a>MACRO

Marca un bloque de macro denominado *Name* y establece marcadores de posición de *parámetros* para los argumentos pasados cuando se llama a la macro.

## <a name="syntax"></a>Sintaxis

> *Name***macro** ⟦*parámetro* ⟦ **: REQ** | : =*valor predeterminado* | *args* **: vararg**⟧... ⟧\
> *instrucciones*\
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦ *⟧*

## <a name="remarks"></a>Observaciones

Una función de macro devuelve un *valor* a la instrucción de llamada.

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Goto (MASM)](goto-masm.md)\
\ [ENDM](endm.md)
[Gramática BNF de MASM](masm-bnf-grammar.md)
