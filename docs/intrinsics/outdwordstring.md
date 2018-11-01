---
title: __outdwordstring
ms.date: 11/04/2016
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: d94db2f59f9a3a8074331054b04cef59cebac0dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502601"
---
# <a name="outdwordstring"></a>__outdwordstring

**Específicos de Microsoft**

Genera el `rep outsd` instrucción, que envía `Count` a partir de palabras dobles `Buffer` fuera del puerto de E/S especificado por `Port`.

## <a name="syntax"></a>Sintaxis

```
void __outdwordstring( 
   unsigned short Port, 
   unsigned long* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] El puerto para enviar los datos.

*búfer*<br/>
[in] Un puntero a los datos se envíen el puerto especificado.

*Recuento*<br/>
[in] El número de palabras dobles para enviar.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)