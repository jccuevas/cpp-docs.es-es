---
title: marshal_context (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136999"
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