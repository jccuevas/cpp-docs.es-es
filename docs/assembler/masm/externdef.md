---
title: EXTERNDEF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5c3d42cabb88c38ce1d98da24cd2cb4ddec8d5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683666"
---
# <a name="externdef"></a>EXTERNDEF

Define uno o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es `type`.

## <a name="syntax"></a>Sintaxis

> Nombre: tipo de EXTERNDEF [[langtype]] [[, [[langtype]]: tipo de nombre]]...

## <a name="remarks"></a>Comentarios

Si *nombre* se define en el módulo, se trata como [pública](../../assembler/masm/public-masm.md). Si *nombre* se hace referencia en el módulo, se trata como [EXTERN](../../assembler/masm/extern-masm.md). Si *nombre* no es hacer referencia, se omite. El `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Se utiliza normalmente en archivos de inclusión.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>