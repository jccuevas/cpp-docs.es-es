---
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: da6ca9786b9c7e5041b9a8ca908d567b16176436
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219816"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Específicos de Microsoft**

Carga un subconjunto de estado del procesador desde el bloque de control de máquina virtual especificado (VMCB).

## <a name="syntax"></a>Sintaxis

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parámetros

*VmcbPhysicalAddress*\
de Dirección física de VMCB.

## <a name="remarks"></a>Comentarios

La función `__svm_vmload` equivale a la instrucción máquina `VMLOAD` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, "número de documento 24593, revisión 3,11, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
