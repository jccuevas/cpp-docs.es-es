---
title: __outbytestring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ef1bb6e4804fc71531f694a3dac4c5504941bf0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393768"
---
# <a name="outbytestring"></a>__outbytestring

**Específicos de Microsoft**

Genera el `rep outsb` instrucción, que envía el primer `Count` bytes de datos apunta a `Buffer` al puerto especificado por `Port`.

## <a name="syntax"></a>Sintaxis

```
void __outbytestring( 
   unsigned short Port, 
   unsigned char* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] El puerto para enviar los datos.

*búfer*<br/>
[in] Los datos se envíen el puerto especificado.

*Recuento*<br/>
[in] El número de bytes de datos que se envían.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)