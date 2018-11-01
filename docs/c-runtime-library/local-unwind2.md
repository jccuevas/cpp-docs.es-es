---
title: _local_unwind2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
dev_langs:
- C++
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47227d4be0ad1c5145a9064d11b4ea633c7d7fc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035791"
---
# <a name="localunwind2"></a>_local_unwind2

Función de CRT interna. Ejecuta todos los controladores de finalización que figuran en la tabla de ámbito indicada.

## <a name="syntax"></a>Sintaxis

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parámetros

*xr*<br/>
[in] Registro asociado a una tabla de ámbito.

*stop*<br/>
[in] Nivel léxico que señala dónde debe detenerse `_local_unwind2`.

## <a name="remarks"></a>Comentarios

Este método solo se usa en el entorno en tiempo de ejecución. No llame a este método en su código.

Cuando este método ejecuta controladores de finalización, comienza en el nivel léxico actual y realiza su recorrido hacia niveles léxicos superiores hasta que alcanza el nivel indicado por `stop`. No ejecuta controladores de finalización situados en el nivel indicado por `stop`.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)