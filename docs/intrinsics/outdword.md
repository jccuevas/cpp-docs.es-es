---
title: __outdword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outdword
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7f7d5cf08ba83f83513f591ce04b1ff527cd491
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420574"
---
# <a name="outdword"></a>__outdword

**Específicos de Microsoft**

Genera el `out` instrucción para enviar una palabra doble `Data` el puerto de salida `Port`.

## <a name="syntax"></a>Sintaxis

```
void __outdword( 
   unsigned short Port, 
   unsigned long Data 
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] El puerto para enviar los datos.

*Data*<br/>
[in] La palabra doble que se enviarán.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__outdword`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)