---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 11/04/2016
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: b3e5664064f9c32d6c5f5a1e6751712bc36cc7b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668564"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Específicos de Microsoft**

Leer la memoria desde una ubicación especificada por un desplazamiento relativo al principio del segmento GS.

## <a name="syntax"></a>Sintaxis

```
unsigned char __readgsbyte( 
   unsigned long Offset 
);
unsigned short __readgsword( 
   unsigned long Offset 
);
unsigned long __readgsdword( 
   unsigned long Offset
);
unsigned __int64 __readgsqword( 
   unsigned long Offset 
);
```

#### <a name="parameters"></a>Parámetros

*Desplazamiento*<br/>
[in] El desplazamiento desde el principio del `GS` a leer.

## <a name="return-value"></a>Valor devuelto

El contenido de la memoria del byte, word, palabra doble o quadword (tal y como se indica el nombre de la función llamado) en la ubicación `GS:[Offset]`.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readgsbyte`|x64|
|`__readgsdword`|x64|
|`__readgsqword`|x64|
|`__readgsword`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Estas funciones intrínsecas solo están disponibles en modo kernel, y las rutinas solo están disponibles como intrínsecos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)