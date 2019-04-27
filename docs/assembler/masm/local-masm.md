---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178012"
---
# <a name="local-masm"></a>LOCAL (MASM)

En la primera directiva dentro de una macro, **LOCAL** define las etiquetas que son únicas para cada instancia de la macro.

## <a name="syntax"></a>Sintaxis

> LOCAL *localname* \[, *localname*]...
>
> LOCAL *etiqueta* \[ __\[__ *recuento*__]__ ] \[ __:__  *tipo*] \[ __,__ *etiqueta* \[ __\[__ *recuento* __]__  ] \[ *tipo*]]...

## <a name="remarks"></a>Comentarios

En la segunda directiva dentro de una definición de procedimiento (**PROC**), **LOCAL** crea variables de pila que existen para la duración del procedimiento. El *etiqueta* puede ser una variable simple o una matriz que contiene *recuento* elementos.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>