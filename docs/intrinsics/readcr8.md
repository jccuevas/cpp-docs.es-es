---
title: __readcr8
ms.date: 09/02/2019
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 525775fde4cb96cecfcabef878780d5a2aa6743a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221235"
---
# <a name="__readcr8"></a>__readcr8

**Específicos de Microsoft**

Lee el registro CR8 y devuelve su valor.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>Valor devuelto

El valor del registro CR8.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readcr8`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El intrínseco solo está disponible en modo kernel y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
