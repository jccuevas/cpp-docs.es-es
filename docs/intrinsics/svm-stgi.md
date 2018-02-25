---
title: __svm_stgi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_stgi
dev_langs:
- C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9346270c09a3174c2583d68cdfb62e11f5112144
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="svmstgi"></a>__svm_stgi
**Específicos de Microsoft**  
  
 Establece la marca global de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>Comentarios  
 El `__svm_stgi` función es equivalente a la `STGI` instrucción máquina. El indicador de interrupción global determina si el microprocesador omite, pospone o controla las interrupciones a causa de eventos como una finalización de E/S, una alerta de temperatura de hardware o una excepción de depuración.  
  
 Esta función admite la interacción del monitor de máquina virtual de un host con un sistema operativo invitado y sus aplicaciones. Para obtener más información, busque el documento "volumen de Manual del programador de arquitectura AMD64 2: programación de sistema," número 24593, 3.11, de revisión del documento en el [corporation AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) sitio.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__svm_stgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)