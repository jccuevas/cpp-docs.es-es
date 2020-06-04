---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219760"
---
# <a name="__ud2"></a>__ud2

**Específicos de Microsoft**

Genera una instrucción sin definir.

## <a name="syntax"></a>Sintaxis

```C
void __ud2();
```

## <a name="remarks"></a>Comentarios

Si ejecuta una instrucción sin definir, el procesador genera una excepción de código de operación no válida.

La `__ud2` función es equivalente a la `UD2` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento "manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__ud2`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se ejecuta una instrucción undefined, que genera una excepción. Después, el controlador de excepciones cambia el código de retorno de cero a uno.

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
