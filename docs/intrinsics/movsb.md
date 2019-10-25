---
title: __movsb
ms.date: 09/02/2019
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: ca06fc9114f6e824a690cc4e612c21d705a485cd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217279"
---
# <a name="__movsb"></a>__movsb

**Específicos de Microsoft**

Genera una instrucción Move String`rep movsb`().

## <a name="syntax"></a>Sintaxis

```C
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

### <a name="parameters"></a>Parámetros

*Destino*\
enuncia Puntero al destino de la copia.

*Source*\
de Puntero al origen de la copia.

*Contabiliza*\
de Número de bytes que se van a copiar.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__movsb`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

El resultado es que los primeros `Count` bytes `Source` a los que apunta se copian `Destination` en la cadena.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```cpp
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

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
