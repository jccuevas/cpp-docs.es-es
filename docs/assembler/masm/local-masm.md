---
title: LOCAL (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685068"
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