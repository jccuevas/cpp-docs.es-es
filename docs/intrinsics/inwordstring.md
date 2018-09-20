---
title: __inwordstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inwordstring
- __inwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969d57d01915ecfcf20c29b08d71c438206c45b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440535"
---
# <a name="inwordstring"></a>__inwordstring

**Específicos de Microsoft**

Lee datos desde el puerto especificado mediante el `rep insw` instrucción.

## <a name="syntax"></a>Sintaxis

```
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] Para leer desde el puerto.

*búfer*<br/>
[out] Los datos leídos desde el puerto se escriben aquí.

*Recuento*<br/>
[in] El número de palabras de datos que se va a leer.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__inwordstring`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)