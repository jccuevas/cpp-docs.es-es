---
title: marshal_context (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: marshal_context
dev_langs: C++
helpviewer_keywords: marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b59dfa82563a0c115f521bb881411981a30efc9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="marshalcontext-class"></a>serializar_context (Clase)
Esta clase convierte los datos entre los entornos nativo y administrados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>Comentarios  
 Use la `marshal_context` clase para las conversiones de datos que requieren un contexto. Vea [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de qué conversiones requieren un contexto y el archivo de cálculo de referencias que se van a incluir. El resultado del cálculo de referencias cuando se usa un contexto es válido solo hasta que la `marshal_context` se destruye el objeto. Para conservar su resultado, debe copiar los datos.  
  
 El mismo `marshal_context` puede usarse para varias conversiones de datos. Volver a usar el contexto de esta manera no afectará a los resultados de las llamadas de cálculo de referencias anteriores.  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\serializar_windows. h >, \<msclr\serializar_cppstd. h >, o \<msclr\serializar_atl. h >  
  
 **Namespace:** msclr:: Interop  
  
## <a name="see-also"></a>Vea también  
 [Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)