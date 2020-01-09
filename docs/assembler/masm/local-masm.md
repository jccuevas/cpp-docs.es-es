---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317154"
---
# <a name="local"></a>LOCAL

En la primera Directiva, en una macro, **local** define las etiquetas que son únicas para cada instancia de la macro.

## <a name="syntax"></a>Sintaxis

> ⟦ *LocalId* **local** , *localId* ... ⟧
>
> **Local** *labelId* ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *qualifiedType*⟧ ⟦ __,__ *labelId* ⟦ __\[__ *Count* __]__ ⟧ ⟦*qualifiedType ⟧.* .. ⟧

## <a name="remarks"></a>Notas

En la segunda Directiva, dentro de una definición de procedimiento (**proc**), **local** crea variables basadas en la pila que existen mientras dure el procedimiento. *LabelId* puede ser una variable simple o una matriz que contenga elementos *Count* , donde *Count* es una expresión constante.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
