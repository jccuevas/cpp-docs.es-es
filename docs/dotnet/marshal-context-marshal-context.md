---
title: 'serializar_context:: serializar_context | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e8838864c4ec1c6414401608b848cb12b01c16e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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