---
title: __readcr3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readcr3
dev_langs: C++
helpviewer_keywords: __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a4769a6391724e8881182b1c9a78191a2f0ca089
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="readcr3"></a>__readcr3
**Específicos de Microsoft**  
  
 Lee el registro de CR3 y devuelve su valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __readcr3(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El valor en el registro de CR3.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__readcr3`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Este intrínseco solo está disponible en modo kernel, y la rutina solo está disponible como intrínseco.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)