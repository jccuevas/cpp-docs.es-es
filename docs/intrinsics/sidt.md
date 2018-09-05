---
title: __sidt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202e982d30fd0877814fa0c0fe967091057f920f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685982"
---
# <a name="sidt"></a>__sidt
**Específicos de Microsoft**  
  
 Almacena el valor del registro de tabla de interrupciones descriptor (IDTR) en la ubicación de memoria especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `Destination`|Un puntero a la ubicación de memoria donde se almacena el IDTR.|  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__sidt`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El `__sidt` función es equivalente a la `SIDT` instrucción máquina. Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: referencia de conjunto de instrucciones," en el [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) sitio.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)