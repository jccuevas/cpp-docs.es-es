---
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: fcd801717974a230fbd19cc7802d8f6a011774f7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221804"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Específicos de Microsoft**

Cuenta el número de ceros a la izquierda en un entero de 16, 32 o 64 bits.

## <a name="syntax"></a>Sintaxis

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Parámetros

*value*\
de Entero de 16, 32 o 64 bits sin signo que se va a examinar para buscar ceros a la izquierda.

## <a name="return-value"></a>Valor devuelto

Número de bits cero iniciales en el `value` parámetro. Si `value` es cero, el valor devuelto es el tamaño del operando de entrada (16, 32 o 64). Si el bit más significativo de `value` es uno, el valor devuelto es cero.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__lzcnt16`|POWERNOW Manipulación de bits avanzada (ABN)<br /><br /> Procesador Haswell|
|`__lzcnt`|POWERNOW Manipulación de bits avanzada (ABN)<br /><br /> Procesador Haswell|
|`__lzcnt64`|POWERNOW Manipulación de bits avanzada (ABN) en modo de 64 bits.<br /><br /> Procesador Haswell|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

Cada una de las funciones intrínsecas `lzcnt` genera la instrucción.  El tamaño del valor que devuelve la `lzcnt` instrucción es el mismo que el tamaño de su argumento.  En el modo de 32 bits, no hay ningún registro de uso general de 64 bits, por lo que no se `lzcnt` admiten los 64 bits.

Para determinar la compatibilidad de hardware `lzcnt` de la instrucción, `__cpuid` llame a `InfoType=0x80000001` la función intrínseca con y `CPUInfo[2] (ECX)`Compruebe el bit 5 de. Este bit será 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta código que usa el intrínseco en hardware que no admite la `lzcnt` instrucción, los resultados son imprevisibles.

En los procesadores Intel que no admiten la `lzcnt` instrucción, la codificación de bytes de la instrucción se ejecuta como `bsr` (recorrido de bits inverso). Si la portabilidad del código es un problema, considere la `_BitScanReverse` posibilidad de usar en su lugar el intrínseco. Para obtener más información, vea [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

## <a name="example"></a>Ejemplo

```cpp
// Compile this test with: /EHsc
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
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**FIN de Específicos de Microsoft**

Algunas partes de este contenido son Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Se reproduce con el permiso de Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
