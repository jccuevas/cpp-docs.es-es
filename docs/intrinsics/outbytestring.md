---
title: __outbytestring
ms.date: 11/04/2016
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 41064dda6a1a0b9ad4c15f98c3f3081f08ef8db6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032198"
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