---
title: 'serializar_context:: serializar_context | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a91b4f1c5f30711c46550dabb4369e380214fce1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="marshalcontextmarshalcontext"></a>serializar_context::serializar_context
Construye un `marshal_context` objeto que se va a usar para la conversión de datos entre los tipos de datos administrados y nativos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
marshal_context();  
```  
  
## <a name="remarks"></a>Comentarios  
 Algunas conversiones de datos requieren un contexto de cálculo de referencias. Vea [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué traducciones requieren un contexto y el archivo de cálculo de referencias que debe incluirse en la aplicación.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [serializar_context:: serializar_as](../dotnet/marshal-context-marshal-as.md).  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\serializar_windows. h >, \<msclr\serializar_cppstd. h >, o \<msclr\serializar_atl. h >  
  
 **Namespace:** msclr:: Interop  
  
## <a name="see-also"></a>Vea también  
 [Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context (Clase)](../dotnet/marshal-context-class.md)