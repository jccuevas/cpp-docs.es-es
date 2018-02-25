---
title: __writedr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57f8e72bd8472ee88db3335a968e4a9ec6fb3998
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="writedr"></a>__writedr
Escribe el valor especificado en el registro de depuración especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `DebugRegister`  
 Registrar un número entre 0 y 7 que identifica la depuración.  
  
 [in] `DebugValue`  
 Registrar un valor para escribir en la depuración.  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones intrínsecas están disponibles solo en modo kernel y las rutinas sólo están disponibles como intrínsecos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__writedr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)