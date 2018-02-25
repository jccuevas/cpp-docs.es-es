---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc4d7e760d45efb9bff8073ea50f555417737cfb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword
**Específicos de Microsoft**  
  
 Agregar un valor a una ubicación de memoria especificada por un desplazamiento relativo al principio de la `GS` segmento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __addgsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addgsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addgsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __addgsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Offset`  
 El desplazamiento desde el principio de `GS`.  
  
 [in] `Data`  
 El valor para agregar a la ubicación de memoria.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__addgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__addgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones intrínsecas están disponibles en modo de kernel sólo y estas rutinas solo están disponibles como intrínsecos.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)   
 [__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)