---
title: . CÓDIGO | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682492"
---
# <a name="code"></a>.CODE

Cuando se usa con [. MODELO](../../assembler/masm/dot-model.md), indica el inicio de un segmento de código.

## <a name="syntax"></a>Sintaxis

> . CÓDIGO [[nombre]]

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`name`|Parámetro opcional que especifica el nombre del segmento de código. El nombre predeterminado es _TEXT pequeña, pequeña, compacto y plana [modelos](../../assembler/masm/dot-model.md). El nombre predeterminado es *modulename*_TEXT para otros modelos.|

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>