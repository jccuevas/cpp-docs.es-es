---
title: . PILA | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95e8d69903fabf60fdb5bc04d90452bdad163a19
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676241"
---
# <a name="stack"></a>.STACK

Cuando se usa con [. MODELO](../../assembler/masm/dot-model.md), define un segmento de pila (con el nombre del segmento de pila). El elemento opcional `size` especifica el número de bytes de la pila (el valor predeterminado es 1.024). El `.STACK` directiva cierra automáticamente la instrucción de la pila.

## <a name="syntax"></a>Sintaxis

> . PILA [[size]]

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>