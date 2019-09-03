---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: e43789d2fbed1bdc52665531c61c6c932a27f5ab
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219145"
---
# <a name="__writeeflags"></a>__writeeflags

Escribe el valor especificado en el registro de estado del programa y del control (EFLAGS).

## <a name="syntax"></a>Sintaxis

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parámetros

*Valor*\
de Valor que se va a escribir en el registro EFLAGS. El `Value` parámetro tiene una longitud de 32 bits para una plataforma de 32 bits y una longitud de 64 bits para una plataforma de 64 bits.

## <a name="remarks"></a>Comentarios

Estas rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
