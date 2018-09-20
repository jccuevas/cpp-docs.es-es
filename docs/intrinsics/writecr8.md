---
title: __writecr8 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr8
dev_langs:
- C++
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a06b34ee7d38e5c0e99181c4af81d925b681ce75
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417311"
---
# <a name="writecr8"></a>__writecr8

**Específicos de Microsoft**

Escribe el valor `Data` al registro CR8.

## <a name="syntax"></a>Sintaxis

```
void writecr8( 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Parámetros

*Data*<br/>
[in] El valor para escribir en el registro CR8.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writecr8`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)