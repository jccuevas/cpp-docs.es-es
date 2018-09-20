---
title: __writeeflags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 875945c4116f99a0a7e8ef53666f432987ba0deb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424552"
---
# <a name="writeeflags"></a>__writeeflags

Escribe el valor especificado en el programa de estado y control (EFLAGS) se registran.

## <a name="syntax"></a>Sintaxis

```
void __writeeflags(unsigned Value);
void __writeeflags(unsigned __int64 Value);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Valor*|[in] El valor para escribir en el registro EFLAGS. El `Value` parámetro es de 32 bits para una plataforma de 32 bits y 64 bits para una plataforma de 64 bits.|

## <a name="remarks"></a>Comentarios

Estas rutinas sólo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)