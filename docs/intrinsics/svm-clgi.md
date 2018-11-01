---
title: __svm_clgi
ms.date: 11/04/2016
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 9f3484cc5cbffea1315d546ced317dfdfceee9e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618894"
---
# <a name="svmclgi"></a>__svm_clgi

**Específicos de Microsoft**

Borra la marca global de interrupción.

## <a name="syntax"></a>Sintaxis

```
void __svm_clgi( void );
```

## <a name="remarks"></a>Comentarios

La función `__svm_clgi` equivale a la instrucción máquina `CLGI` . El indicador de interrupción global determina si el microprocesador omite, pospone o controla las interrupciones debidos a eventos como la finalización de E/S, una alerta de temperatura de hardware o una excepción de depuración.

Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: sistema de programación," número 24593, 3.11, revisión del documento en el [corporation AMD](https://developer.amd.com/resources/developer-guides-manuals/) sitio.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_stgi](../intrinsics/svm-stgi.md)