---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08cd68256e1219df36ce6f9ea22165938fba44af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Específicos de Microsoft**  
  
 Escribe el valor especificado en el campo especificado en la estructura de control de máquina virtual (VMCS) actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `Field`|El campo VMCS que se va a escribir.|  
|[in] `FieldValue`|El valor para escribir en el campo VMCS.|  
  
## <a name="return-value"></a>Valor devuelto  
 0  
 La operación se realizó correctamente.  
  
 1  
 Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.  
  
 2  
 Error en la operación sin estado disponible.  
  
## <a name="remarks"></a>Comentarios  
 El `__vmx_vmwrite` función es equivalente a la `VMWRITE` instrucción máquina. El valor de la `Field` parámetro es un índice de campo codificado que se describe en la documentación de Intel. Para obtener más información, busque el documento, "Intel Virtualization técnica especificación para la arquitectura IA-32 Intel," documento número C97063-002 en el [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) de sitio y, a continuación, consulte el apéndice C de ese documento.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)