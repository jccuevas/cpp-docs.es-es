---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f52c2c2ca60f66218b669201f293ca377d4ca5a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707023"
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
|*Campo*|[in] El campo VMCS a escribir.|  
|*FieldValue*|[in] El valor para escribir en el campo VMCS.|  
  
## <a name="return-value"></a>Valor devuelto  
 0  
 La operación se realizó correctamente.  
  
 1  
 Error en la operación con el estado extendido disponible en el `VM-instruction error field` de la VMCS actual.  
  
 2  
 Error en la operación sin estado disponible.  
  
## <a name="remarks"></a>Comentarios  
 El `__vmx_vmwrite` función es equivalente a la `VMWRITE` instrucción máquina. El valor de la `Field` parámetro es un índice de campo codificado que se describe en la documentación de Intel. Para obtener más información, busque el documento, "Intel Virtualization Technical especificación para la arquitectura IA-32 Intel," documento C97063-002, número en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) de sitio y, a continuación, consulte el apéndice C de la que documento.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__vmx_vmwrite`|x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)