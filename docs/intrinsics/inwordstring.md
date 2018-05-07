---
title: __inwordstring | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inwordstring
- __inwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 073c1303661aece3340f9ac84d37ccf23e29d556
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="inwordstring"></a>__inwordstring
**Específicos de Microsoft**  
  
 Lee datos desde el puerto especificado con el `rep insw` instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Port`  
 El puerto que leer.  
  
 [out] `Buffer`  
 Aquí se escriben los datos que se leen del puerto.  
  
 [in] `Count`  
 El número de palabras de datos que se va a leer.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__inwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)