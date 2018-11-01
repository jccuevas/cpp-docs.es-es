---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596877"
---
# <a name="local-masm"></a>LOCAL (MASM)

En la primera directiva dentro de una macro, **LOCAL** define las etiquetas que son únicas para cada instancia de la macro.

## <a name="syntax"></a>Sintaxis

> LOCAL *localname* [[, *localname*]]...

> LOCAL *etiqueta* [[[*recuento*]]] [[:*tipo*]] [[, *etiqueta* [[[*recuento*]]] [[ *tipo*]]]]...

## <a name="remarks"></a>Comentarios

En la segunda directiva dentro de una definición de procedimiento (**PROC**), **LOCAL** crea variables de pila que existen para la duración del procedimiento. El *etiqueta* puede ser una variable simple o una matriz que contiene *recuento* elementos.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>