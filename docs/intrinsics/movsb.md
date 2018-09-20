---
title: __movsb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __movsb
dev_langs:
- C++
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3488815f31f8148c21ebf2242ef85773505a316c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387684"
---
# <a name="movsb"></a>__movsb

**Específicos de Microsoft**

Genera una cadena de mover (`rep movsb`) instrucción.

## <a name="syntax"></a>Sintaxis

```
void __movsb( 
   unsigned char* Destination, 
   unsigned const char* Source, 
   size_t Count 
);
```

#### <a name="parameters"></a>Parámetros

*Destino*<br/>
[out] Un puntero al destino de la copia.

*Source*<br/>
[in] Un puntero al origen de la copia.

*Recuento*<br/>
[in] El número de bytes para copiar.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__movsb`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El resultado es que la primera `Count` bytes señalada por `Source` se copian en el `Destination` cadena.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)