---
title: __svm_invlpga | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0343222a08b1ab192be733a1f583cc287a9d3377
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="svminvlpga"></a>__svm_invlpga
**Específicos de Microsoft**  
  
 Invalida la entrada de asignación de dirección en el búfer de consulta de traducción del equipo. Los parámetros especifican la dirección virtual y el identificador de espacio de dirección de la página para invalidar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `Va`|La dirección virtual de la página para invalidar.|  
|[in] `ASID`|El identificador de espacio de dirección (ASID) de la página para invalidar.|  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_invlpga` función es equivalente a la `INVLPGA` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen de Manual del programador de arquitectura AMD64 2: programación de sistema," número 24593, 3.11, de revisión del documento en el [corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_invlpga`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)