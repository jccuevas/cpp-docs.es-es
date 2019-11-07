---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702465"
---
# <a name="assume-32-bit-masm"></a>Suponer (MASM de 32 bits)

Habilita la comprobación de errores para los valores de registro. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> ASUMA *segregister*:*nombre* [[, *segregister*:*nombre*]]...<br/>
> Supongamos que se ha *registrado*la:*tipo* [[, *registro de registros*:*tipo*]]...<br/>
> Supongamos que se ha *registrado*: error [[, *Register*: error]]...<br/>
> ASUMA [[*Register*:]] Nothing [[, *Register*: Nothing]]...

## <a name="remarks"></a>Comentarios

Una vez que se aplica un `ASSUME`, el ensamblador inspecciona los cambios en los valores de los registros especificados. El **error** genera un error si se usa el registro. **Nada** quita la comprobación de errores de registro. Puede combinar diferentes tipos de suposiciones en una instrucción.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>