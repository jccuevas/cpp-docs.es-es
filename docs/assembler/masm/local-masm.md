---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397255"
---
# <a name="local-masm"></a>LOCAL (MASM)

En la primera Directiva, en una macro, **local** define las etiquetas que son únicas para cada instancia de la macro.

## <a name="syntax"></a>Sintaxis

> **Local** *localname* ⟦, *localname* ... ⟧
>
> *Etiqueta* local ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *Type*⟧ ⟦ __,__ *Label* ⟦ __\[__ *Count* __]__ ⟧ ⟦*Type*⟧... ⟧

## <a name="remarks"></a>Comentarios

En la segunda Directiva, dentro de una definición de procedimiento (**proc**), **local** crea variables basadas en la pila que existen mientras dure el procedimiento. La *etiqueta* puede ser una variable simple o una matriz que contenga elementos de *recuento* .

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
