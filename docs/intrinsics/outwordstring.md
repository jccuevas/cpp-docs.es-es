---
title: __outwordstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outwordstring
dev_langs:
- C++
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d148f6b2b6078693e5e05c02310c3e52e710b3e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392702"
---
# <a name="outwordstring"></a>__outwordstring

**Específicos de Microsoft**

Genera el `rep outsw` instrucción, que envía `Count` palabras que empiezan en `Buffer` fuera del puerto de E/S especificado por `Port`.

## <a name="syntax"></a>Sintaxis

```
void __outwordstring( 
   unsigned short Port, 
   unsigned short* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] El puerto para enviar los datos.

*búfer*<br/>
[in] Un puntero a los datos se envíen el puerto especificado.

*Recuento*<br/>
[in] El número de palabras para enviar.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)