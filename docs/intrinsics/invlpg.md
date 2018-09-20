---
title: __invlpg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01a35d110c56bba6b89c5bf34dedec61bde90794
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403219"
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