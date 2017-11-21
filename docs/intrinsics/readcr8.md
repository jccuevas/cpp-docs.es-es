---
title: __readcr8 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readcr8
dev_langs: C++
helpviewer_keywords: __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d05200d031da60ebd32707648a260b511ba4088
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="readcr8"></a>__readcr8
**Específicos de Microsoft**  
  
 Lee el registro de CR8 y devuelve su valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __readcr8(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El valor en el registro de CR8.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__readcr8`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)