---
title: __nop | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __nop
dev_langs: C++
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aecf1c0ad205d2cbf0685797cc9527f1fc4684d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="nop"></a>__nop
**Específicos de Microsoft**  
  
 Genera código máquina específico de plataforma que no realiza ninguna operación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __nop();  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__nop`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="remarks"></a>Comentarios  
 El `__nop` función es equivalente a la `NOP` instrucción máquina. Para obtener más información, busque el documento "Manual del desarrollador de Software de arquitectura Intel, volumen 2: referencia de conjunto de instrucciones," en el [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) sitio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__noop](../intrinsics/noop.md)