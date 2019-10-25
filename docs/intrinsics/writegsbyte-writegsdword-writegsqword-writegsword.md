---
title: __writegsbyte, __writegsdword, __writegsqword, __writegsword
ms.date: 09/02/2019
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
ms.openlocfilehash: 7b9e812776e9b2bb0820905d088111669096db64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221201"
---
# <a name="__writegsbyte-__writegsdword-__writegsqword-__writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword

**Específicos de Microsoft**

Escribe memoria en una ubicación especificada por un desplazamiento relativo al principio del segmento GS.

## <a name="syntax"></a>Sintaxis

```C
void __writegsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writegsword(
   unsigned long Offset,
   unsigned short Data
);
void __writegsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writegsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parámetros

*Posición*\
de Desplazamiento desde el principio de GS en el que se va a escribir.

*Data*\
de Valor que se va a escribir.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writegsbyte`|x64|
|`__writegsdword`|x64|
|`__writegsqword`|x64|
|`__writegsword`|x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Estas rutinas solo están disponibles como intrínsecos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
