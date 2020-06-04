---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219857"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Específicos de Microsoft**

Inicia la carga de software seguro y comprobable, como un monitor de máquina virtual.

## <a name="syntax"></a>Sintaxis

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>Parámetros

*block_address*\
Dirección física de 32 bits de un bloque de cargador seguro (SLB) de 64 bytes.

## <a name="remarks"></a>Comentarios

La función `__svm_skinit` equivale a la instrucción máquina `SKINIT` . Esta función forma parte de un sistema de seguridad que usa el procesador y un Módulo de plataforma segura (TPM), para comprobar y cargar software de confianza, denominado *kernel de seguridad* (SK). Un monitor de máquina virtual es un ejemplo de un kernel de seguridad. El sistema de seguridad comprueba los componentes de programa cargados durante el proceso de inicialización. Protege los componentes contra alteraciones por interrupciones, acceso a dispositivos u otro programa si el equipo es un multiprocesador.

El parámetro *block_address* especifica la dirección física de un bloque de memoria de 64K denominado *bloque de cargador seguro* (SLB). El SLB contiene un programa denominado *cargador seguro*. Establece el entorno operativo del equipo y, a continuación, carga el kernel de seguridad.

Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque "volumen manual del programador de arquitectura AMD64 2: Programación del sistema, en el sitio de [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
