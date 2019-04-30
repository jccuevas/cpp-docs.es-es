---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: b4f941baae9f03ed288a99d59e2b06262962e339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348749"
---
# <a name="invlpg"></a>__invlpg

**Específicos de Microsoft**

Genera el x86 `invlpg` instrucción, lo que invalida el búfer de traducción de direcciones (TLB) para la página asociada a la memoria que apunta `Address`.

## <a name="syntax"></a>Sintaxis

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>Parámetros

*Dirección*<br/>
[in] Una dirección de 64 bits.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

La función intrínseca `__invlpg` emite una instrucción privilegiada y solo está disponible en modo kernel con un nivel de privilegios (CPL) de 0.

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)