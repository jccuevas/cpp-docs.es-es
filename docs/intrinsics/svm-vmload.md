---
title: __svm_vmload
ms.date: 11/04/2016
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: 282f1c005c7eb59b2c590c70b38233c88c664e07
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031159"
---
# <a name="svmvmload"></a>__svm_vmload

**Específicos de Microsoft**

Carga un subconjunto de estado de procesador desde el bloque de control de máquina virtual especificada (VMCB).

## <a name="syntax"></a>Sintaxis

```
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] La dirección física de la VMCB.|

## <a name="remarks"></a>Comentarios

La función `__svm_vmload` equivale a la instrucción máquina `VMLOAD` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: Sistema de programación,"número 24593, 3.11, revisión del documento en el [corporation AMD](https://developer.amd.com/resources/developer-guides-manuals/) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmrun](../intrinsics/svm-vmrun.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)