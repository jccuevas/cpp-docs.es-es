---
title: __lidt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4b6dcdee1d30274e8cc4baf3de70e4c6cbb611d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692707"
---
# <a name="lidt"></a>__lidt
**Específicos de Microsoft**  
  
 Carga el registro de tabla del descriptor de interrupción (IDTR) con el valor en la ubicación de memoria especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `Source`|Puntero al valor que se copiarán en el IDTR.|  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__lidt`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El `__lidt` función es equivalente a la `LIDT` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: referencia de conjunto de instrucciones," en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) sitio.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)