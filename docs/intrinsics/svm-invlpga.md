---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219887"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Específicos de Microsoft**

Invalida la entrada de asignación de direcciones en el búfer de la búsqueda de traducciones del equipo. Los parámetros especifican la dirección virtual y el identificador del espacio de direcciones de la página que se va a invalidar.

## <a name="syntax"></a>Sintaxis

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>Parámetros

*Vaddr*\
de Dirección virtual de la página que se va a invalidar.

*as_id*\
de Identificador del espacio de direcciones (ASID) de la página que se va a invalidar.

## <a name="remarks"></a>Comentarios

La función `__svm_invlpga` equivale a la instrucción máquina `INVLPGA` . Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, "número de documento 24593, revisión 3,11, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
