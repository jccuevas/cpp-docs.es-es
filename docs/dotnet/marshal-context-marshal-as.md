---
title: 'serializar_context:: serializar_as | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 27f27b164d7a00e05e8d080a692f97b696776cbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontextmarshalas"></a>serializar_context::serializar_as
Realiza el cálculo de referencias en un objeto de datos específico para convertir entre administrado y un tipo de datos nativos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `input`  
 El valor cuyas referencias desea calcular para una variable `To_Type`.  
  
## <a name="return-value"></a>Valor devuelto  
 Una variable de tipo `To_Type` que es el valor convertido de `input`.  
  
## <a name="remarks"></a>Comentarios  
 Esta función realiza el cálculo de referencias en un objeto de datos específicos. Utilice esta función sólo con las conversiones que se indican en la tabla de [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Si se intenta serializar un par de tipos de datos que no son compatibles, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las desusadas. Dos condiciones que se generarán este error se intenta serializar un par de tipos de datos que no son compatibles y que va a usar `marshal_as` para realizar una conversión que requiere un contexto.  
  
 La biblioteca de serialización se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. La tabla de `Marshaling Overview in C++` indica qué archivo de cálculo de referencias debe incluirse en cada conversión.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo crea un contexto de serialización de un `System::String` a una `const char *` tipo de variable. Los datos convertidos no será válidos después de la línea que elimina el contexto.  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\serializar_windows. h >, \<msclr\serializar_cppstd. h >, o \<msclr\serializar_atl. h >  
  
 **Namespace:** msclr:: Interop  
  
## <a name="see-also"></a>Vea también  
 [Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context (Clase)](../dotnet/marshal-context-class.md)