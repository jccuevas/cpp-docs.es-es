---
title: INSTR | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- InStr
dev_langs:
- C++
helpviewer_keywords:
- INSTR directive
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f540b7fffb23321c8b3aa22e154196c48f76cd58
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683063"
---
# <a name="instr"></a>INSTR

Busca la primera aparición de *textitem2* en *textitem1*.

## <a name="syntax"></a>Sintaxis

> *nombre* INSTR [[*posición*,]] *textitem1*, *textitem2*

## <a name="remarks"></a>Comentarios

El inicio *posición* es opcional. Cada elemento de texto puede ser una cadena literal, una constante precedida por un `%`, o la cadena devuelta por una función de macro.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>