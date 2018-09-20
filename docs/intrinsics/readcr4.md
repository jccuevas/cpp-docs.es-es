---
title: __readcr4 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr4
dev_langs:
- C++
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7089a92e87449acbafe93bec8a2190a425a843a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411081"
---
# <a name="readcr4"></a>__readcr4

**Específicos de Microsoft**

Lee el registro CR4 y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Valor devuelto

El valor del registro CR4.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)