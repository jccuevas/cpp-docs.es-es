---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221360"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Específicos de Microsoft**

Cuenta el número de `1` bits (número de rellenado) en un entero de 16, 32 o 64 bits sin signo.

## <a name="syntax"></a>Sintaxis

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Parámetros

*value*\
de Entero de 16, 32 o 64 bits sin signo para el que se desea el recuento de población.

## <a name="return-value"></a>Valor devuelto

Número de `1` bits del parámetro de *valor* .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__popcnt16`|Manipulación de bits avanzada|
|`__popcnt`|Manipulación de bits avanzada|
|`__popcnt64`|Manipulación de bits avanzada en modo de 64 bits.|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Cada una de las funciones intrínsecas `popcnt` genera la instrucción. En el modo de 32 bits, no hay registros de uso general de 64 bits, por lo que no se `popcnt` admite 64 bits.

Para determinar la compatibilidad de hardware `popcnt` de la instrucción, `__cpuid` llame a `InfoType=0x00000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 23 de. Este bit es 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta código que usa estos intrínsecos en hardware que no admite la `popcnt` instrucción, los resultados son imprevisibles.

## <a name="example"></a>Ejemplo

```cpp
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**FIN de Específicos de Microsoft**

Partes con Copyright 2007 de Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
