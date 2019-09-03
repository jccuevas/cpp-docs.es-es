---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219833"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Específicos de Microsoft**

Establece la marca de interrupción global.

## <a name="syntax"></a>Sintaxis

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Comentarios

La función `__svm_stgi` equivale a la instrucción máquina `STGI` . La marca de interrupción global determina si el microprocesador omite, pospone o controla las interrupciones, debido a eventos como una finalización de e/s, una alerta de temperatura de hardware o una excepción de depuración.

Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
