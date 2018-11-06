---
title: __writemsr
ms.date: 11/04/2016
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: ce73d472f71000695ffb6091325d34dfc673e1d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662116"
---
# <a name="writemsr"></a>__writemsr

**Específicos de Microsoft**

Genera la escritura en Model Specific Register (`wrmsr`) instrucción.

## <a name="syntax"></a>Sintaxis

```
void __writemsr( 
   unsigned long Register, 
   unsigned __int64 Value 
);
```

#### <a name="parameters"></a>Parámetros

*Registro*<br/>
[in] El registro específico del modelo.

*Valor*<br/>
[in] El valor para escribir.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función solo puede usarse en modo kernel, y esta rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)