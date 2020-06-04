---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858053"
---
# <a name="__writeeflags"></a>__writeeflags

**Específicos de Microsoft**

Escribe el valor especificado en el registro de estado del programa y del control (EFLAGS).

## <a name="syntax"></a>Sintaxis

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parameters

*Value*\
de Valor que se va a escribir en el registro EFLAGS. El parámetro `Value` tiene una longitud de 32 bits para una plataforma de 32 bits y una longitud de 64 bits para una plataforma de 64 bits.

## <a name="remarks"></a>Notas

Estas rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
