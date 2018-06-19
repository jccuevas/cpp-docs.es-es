---
title: 'serializar_context:: ~ serializar_context | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6cb7ed3c7b1ee5b28c4943d83b6a8ca6166b6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138093"
---
# <a name="marshalcontextmarshalcontext"></a>serializar_context::~serializar_context
Destruye un objeto `marshal_context`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>Comentarios  
 Algunas conversiones de datos requieren un contexto de cálculo de referencias. Vea [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué traducciones requieren un contexto y el archivo de cálculo de referencias que debe incluirse en la aplicación.  
  
 Eliminar un `marshal_context` objeto invalidará los datos convertidos por ese contexto. Si desea conservar los datos después de un `marshal_context` se destruye el objeto, debe copiar manualmente los datos a una variable que se conservará.  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\serializar_windows. h >, \<msclr\serializar_cppstd. h >, o \<msclr\serializar_atl. h >  
  
 **Namespace:** msclr:: Interop  
  
## <a name="see-also"></a>Vea también  
 [Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context (Clase)](../dotnet/marshal-context-class.md)