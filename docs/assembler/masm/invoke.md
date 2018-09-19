---
title: INVOCAR | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5698acf9986903a1d6d731c1047484a0ce6904
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676522"
---
# <a name="invoke"></a>INVOKE

Llama al procedimiento en la dirección proporcionada por *expresión*, pasando los argumentos en la pila o en los registros según las convenciones de llamada estándares del tipo de lenguaje.

## <a name="syntax"></a>Sintaxis

> INVOKE *expresión* [[, *argumentos*]]

## <a name="remarks"></a>Comentarios

Cada argumento pasado al procedimiento puede ser una expresión, un par de registro o una expresión de dirección (precedido de una expresión `ADDR`).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>