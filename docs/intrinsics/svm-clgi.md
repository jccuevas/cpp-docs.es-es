---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219970"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Específicos de Microsoft**

Borra la marca de interrupción global.

## <a name="syntax"></a>Sintaxis

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Comentarios

La función `__svm_clgi` equivale a la instrucción máquina `CLGI` . La marca de interrupción global determina si el microprocesador omite, pospone o controla las interrupciones, debido a eventos como una finalización de e/s, una alerta de temperatura de hardware o una excepción de depuración.

Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
