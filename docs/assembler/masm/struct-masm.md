---
title: STRUCT (MASM)
ms.date: 12/17/2019
f1_keywords:
- struct
helpviewer_keywords:
- STRUCT directive
ms.assetid: 70c3ba6b-00db-461e-8dd9-eafd3ae5b3c8
ms.openlocfilehash: f253c95eca6a3d48a4d9a7f3a7a4e97ea41202c8
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825465"
---
# <a name="struct"></a>STRUCT

Declara un tipo de estructura con las *declaraciones de campo*especificadas. Cada campo debe ser una definición de datos válida. Igual que [STRUC](struc.md).

## <a name="syntax"></a>Sintaxis

> *nombre* **struct** ⟦*alignment*⟧ ⟦__,__ **ununique**⟧ \
> *declaraciones de campo*\
> *nombre* **finaliza**

## <a name="remarks"></a>Observaciones

El argumento *Name* debe ser el mismo en la instrucción de apertura y cierre.

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
