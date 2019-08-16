---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203102"
---
# <a name="externdef"></a>EXTERNDEF

Define uno o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es `type`.

## <a name="syntax"></a>Sintaxis

> Nombre: tipo de EXTERNDEF [[langtype]] [[, [[langtype]]: tipo de nombre]]...

## <a name="remarks"></a>Comentarios

Si *nombre* se define en el módulo, se trata como [pública](../../assembler/masm/public-masm.md). Si *nombre* se hace referencia en el módulo, se trata como [EXTERN](../../assembler/masm/extern-masm.md). Si *nombre* no es hacer referencia, se omite. El `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Se utiliza normalmente en archivos de inclusión.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>