---
title: __inbytestring
ms.date: 09/02/2019
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: cb6e811c809c6069c47415e87804641f30a3897b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217813"
---
# <a name="__inbytestring"></a>__inbytestring

**Específicos de Microsoft**

Lee datos del puerto especificado mediante la `rep insb` instrucción.

## <a name="syntax"></a>Sintaxis

```C
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parámetros

*Casilla*\
de Puerto desde el que se va a leer.

*Búfer*\
enuncia Aquí se escriben los datos leídos del puerto.

*Contabiliza*\
de Número de bytes de datos que se van a leer.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__inbytestring`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Esta rutina solo está disponible como función intrínseca.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
