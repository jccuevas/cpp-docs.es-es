---
title: __vmx_off | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_off
dev_langs:
- C++
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 885df9a8e5e4cb1334a3f18acaf2513d64b91724
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="vmxoff"></a>__vmx_off
**Específicos de Microsoft**  
  
 Desactiva la operación de extensiones (VMX) de la máquina virtual en el procesador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __vmx_off();  
```  
  
## <a name="remarks"></a>Comentarios  
 El `__vmx_off` función es equivalente a la `VMXOFF` instrucción máquina. Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento, "Intel Virtualization técnica especificación para la arquitectura IA-32 Intel," documento número C97063-002 en el [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_off`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)