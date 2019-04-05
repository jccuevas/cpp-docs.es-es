---
title: __svm_invlpga
ms.date: 11/04/2016
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: 5e470fc12ad47aa156c513b293543fa356398d5e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031143"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Específicos de Microsoft**

Invalida la entrada de asignación de direcciones en el búfer de consulta de traducción del equipo. Los parámetros especifican la dirección virtual y el identificador de espacio de direcciones de la página que se va a invalidar.

## <a name="syntax"></a>Sintaxis

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Va*|[in] La dirección virtual de la página que se va a invalidar.|
|*ASID*|[in] El identificador de espacio de dirección (ASID) de la página que se va a invalidar.|

## <a name="remarks"></a>Comentarios

La función `__svm_invlpga` equivale a la instrucción máquina `INVLPGA` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: Sistema de programación,"número 24593, 3.11, revisión del documento en el [corporation AMD](https://developer.amd.com/resources/developer-guides-manuals/) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)