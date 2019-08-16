---
title: __writeeflags
ms.date: 11/04/2016
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6679a3b16def3ed413c5cec2a4bb7d5fe5d732c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389923"
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