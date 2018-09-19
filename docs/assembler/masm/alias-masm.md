---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691067"
---
# <a name="alias-masm"></a>ALIAS (MASM)

El **ALIAS** directiva crea un nombre alternativo para una función.  Esto le permite crear varios nombres para una función o crear bibliotecas que permiten al vinculador (LINK.exe) para asignar una función antigua a una nueva función.

## <a name="syntax"></a>Sintaxis

> ALIAS \< *alias*> = \< *nombre real*>

#### <a name="parameters"></a>Parámetros

*nombre real*<br/>
El nombre real de la función o procedimiento.  Son necesarios los corchetes angulares.

*alias*<br/>
El nombre alternativo o alias.  Son necesarios los corchetes angulares.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>