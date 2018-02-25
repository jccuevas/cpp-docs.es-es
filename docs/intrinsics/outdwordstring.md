---
title: __outdwordstring | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __outdwordstring
dev_langs:
- C++
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5123356cbe04efe7166d7d6688a454ccf7cb5101
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="outdwordstring"></a>__outdwordstring
**Específicos de Microsoft**  
  
 Genera el `rep outsd` instrucción, lo que envía `Count` palabras dobles a partir de `Buffer` fuera del puerto de E/S especificado por `Port`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Port`  
 El puerto para enviar los datos.  
  
 [in] `Buffer`  
 Un puntero a los datos que se envía el puerto especificado.  
  
 [in] `Count`  
 El número de palabras dobles para enviar.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__outdwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)