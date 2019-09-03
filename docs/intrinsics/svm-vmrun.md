---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219824"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Específicos de Microsoft**

Inicia la ejecución del código de invitado de la máquina virtual que corresponde al bloque de control de máquina virtual especificado (VMCB).

## <a name="syntax"></a>Sintaxis

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parámetros

*VmcbPhysicalAddress*\
de Dirección física de VMCB.

## <a name="remarks"></a>Comentarios

La `__svm_vmrun` función usa una cantidad mínima de información en VMCB para empezar a ejecutar el código de invitado de la máquina virtual. Use la función [__svm_vmsave](../intrinsics/svm-vmsave.md) o [__svm_vmload](../intrinsics/svm-vmload.md) si necesita más información para controlar una interrupción compleja o para cambiar a otra invitado.

La función `__svm_vmrun` equivale a la instrucción máquina `VMRUN` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, "número de documento 24593, revisión 3,11 o posterior, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
