---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222149"
---
# <a name="__halt"></a>__halt

**Específicos de Microsoft**

Detiene el microprocesador hasta que se produzca una interrupción habilitada, una interrupción no enmascarable (NMI) o un restablecimiento.

## <a name="syntax"></a>Sintaxis

```C
void __halt( void );
```

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__halt`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

La `__halt` función es equivalente a la `HLT` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento "manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
