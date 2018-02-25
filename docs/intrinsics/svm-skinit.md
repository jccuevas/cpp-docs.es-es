---
title: __svm_skinit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 918bd300e11c52b7b4139cfc80b12a5de2b828a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="svmskinit"></a>__svm_skinit
**Específicos de Microsoft**  
  
 Inicia la carga de software seguro comprobable, por ejemplo, un monitor de máquina virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`SLB`|La dirección física de 32 bits de un byte de 64K bloque de cargador seguro (SLB).|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_skinit` función es equivalente a la `SKINIT` instrucción máquina. Esta función forma parte de un sistema de seguridad que utiliza el procesador y un módulo de plataforma de confianza (TPM) para comprobar y cargar software confianza llamado a un núcleo de seguridad (SK). Un monitor de máquina virtual es un ejemplo de un núcleo de seguridad. El sistema de seguridad comprueba los componentes de programa cargadas durante el proceso de inicialización y protege los componentes contra la manipulación por interrupciones, acceso al dispositivo u otro programa, si el equipo es un multiprocesador.  
  
 El `SLB` parámetro especifica la dirección física de un bloque de 64 KB de memoria caché denominada el *seguros cargador bloque* (SLB). El SLB contiene un programa llamado el cargador seguro que establece el entorno operativo para el equipo y posteriormente se carga el núcleo de seguridad.  
  
 Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen de Manual del programador de arquitectura AMD64 2: programación de sistema," número 24593, 3.11, de revisión del documento en el [corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_skinit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)