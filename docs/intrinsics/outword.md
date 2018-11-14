---
title: __outword
ms.date: 11/04/2016
f1_keywords:
- __outword
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
ms.openlocfilehash: 8a34dfe8bfaedf8f6df5e6f26015eeccd67ed957
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332015"
---
# <a name="outword"></a>__outword

**Específicos de Microsoft**

Genera el `out` instrucción, que envía la palabra `Data` fuera del puerto de E/S especificado por `Port`.

## <a name="syntax"></a>Sintaxis

```
void __outword(
   unsigned short Port,
   unsigned short Data
);
```

#### <a name="parameters"></a>Parámetros

*Puerto*<br/>
[in] El puerto para enviar los datos.

*Data*<br/>
[in] Los datos se envíen.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__outword`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)