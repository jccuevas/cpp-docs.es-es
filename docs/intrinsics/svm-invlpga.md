---
title: __svm_invlpga | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77ada66d0478996eac30c8218793d962e8fcf7ca
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680093"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Específicos de Microsoft**  
  
 Invalida la entrada de asignación de direcciones en el búfer de consulta de traducción del equipo. Los parámetros especifican la dirección virtual y el identificador de espacio de direcciones de la página que se va a invalidar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `Va`|La dirección virtual de la página que se va a invalidar.|  
|[in] `ASID`|El identificador de espacio de dirección (ASID) de la página que se va a invalidar.|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_invlpga` función es equivalente a la `INVLPGA` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "volumen de Manual de programadores de arquitecturas AMD64 2: sistema de programación," número 24593, 3.11, revisión del documento en el [corporation AMD](https://developer.amd.com/resources/developer-guides-manuals/) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_invlpga`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)