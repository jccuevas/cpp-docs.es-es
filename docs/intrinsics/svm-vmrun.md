---
title: __svm_vmrun
ms.date: 11/04/2016
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: ffedf366453a800ce420914376b8d9bb441a602a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603568"
---
# <a name="svmvmrun"></a>__svm_vmrun

**Específicos de Microsoft**

Inicia la ejecución del código de invitado de máquina virtual que se corresponde con el bloque de control de máquina virtual especificada (VMCB).

## <a name="syntax"></a>Sintaxis

```
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] La dirección física de la VMCB.|

## <a name="remarks"></a>Comentarios

El `__svm_vmrun` función usa una cantidad mínima de información en el VMCB para empezar a ejecutar el código de invitado de máquina virtual. Use la [__svm_vmsave](../intrinsics/svm-vmsave.md) o [__svm_vmload](../intrinsics/svm-vmload.md) funcionando si necesita más información para controlar una interrupción compleja o para cambiar a otro invitado.

La función `__svm_vmrun` equivale a la instrucción máquina `VMRUN` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: sistema de programación," número de documento 24593, revisión 3.11 o posterior, en el [corporation AMD](https://developer.amd.com/resources/developer-guides-manuals/) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)