---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: 64ed92af32caaf579e7c6951250e3bf692d1cf43
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944208"
---
# <a name="_local_unwind2"></a>_local_unwind2

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
