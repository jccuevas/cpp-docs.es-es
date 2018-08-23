---
title: __readdr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd45e8919e7b1f0347511e2c3ad782975ecbe71a
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540904"
---
# <a name="readdr"></a>__readdr
Lee el valor del registro de depuración especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `DebugRegister`  
 Registrar una constante de 0 a 7 que identifica la depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor del registro de depuración especificado.  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones intrínsecas están disponibles solo en modo kernel, y las rutinas sólo están disponibles como intrínsecos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__readdr`|x86, x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)