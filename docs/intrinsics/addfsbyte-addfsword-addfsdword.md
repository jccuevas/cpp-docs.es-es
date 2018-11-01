---
title: __addfsbyte, __addfsword, __addfsdword
ms.date: 11/04/2016
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: ccbf604b13db3d40b8ee62c18db1a71e615c79ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505409"
---
# <a name="addfsbyte-addfsword-addfsdword"></a>__addfsbyte, __addfsword, __addfsdword

**Específicos de Microsoft**

Agregar un valor a una ubicación de memoria especificada por un desplazamiento relativo al principio de la `FS` segmento.

## <a name="syntax"></a>Sintaxis

```
void __addfsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addfsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addfsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
```

#### <a name="parameters"></a>Parámetros

*Desplazamiento*<br/>
[in] El desplazamiento desde el principio del `FS`.

*Data*<br/>
[in] Valor que se agrega a la ubicación de memoria.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

## <a name="remarks"></a>Comentarios

Estas rutinas sólo están disponibles como intrínsecos.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)<br/>
[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)