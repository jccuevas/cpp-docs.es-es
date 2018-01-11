---
title: marshal_as | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs: C++
helpviewer_keywords: marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a209b1ee657d6ae6773ee88c64225a7dc5b4f49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="marshalas"></a>serializar_as
Este método convierte los datos entre los entornos nativo y administrado.  
  
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
 Este método es una manera simplificada de convertir datos entre los tipos nativos y administrados. Para determinar qué tipos de datos son compatibles, consulte [información general de serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md). Algunas conversiones de datos requieren un contexto. Puede convertir los tipos de datos mediante la [marshal_context (clase)](../dotnet/marshal-context-class.md).  
  
 Si se intenta serializar un par de tipos de datos que no son compatibles, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación. Lea el mensaje proporcionado con el error para obtener más información. El error `C4996` se puede generar para algunas funciones, aparte de las desusadas. Un ejemplo de esto consiste en intentar para serializar un par de tipos de datos que no se admiten.  
  
 La biblioteca de cálculo de referencias se compone de varios archivos de encabezado. Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones. Para ver qué conversiones están asociadas con qué archivos, consulte la tabla de `Marshaling Overview`. Independientemente de la conversión que desee hacer, el requisito de espacio de nombres siempre está en vigor.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo calcula las referencias de `const char*` para un tipo de variable `System::String`.  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado:** \<msclr\marshal. h >, \<msclr\serializar_windows. h >, \<msclr\serializar_cppstd. h >, o \<msclr\serializar_atl. h >  
  
 **Namespace:** msclr:: Interop  
  
## <a name="see-also"></a>Vea también  
 [Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context (Clase)](../dotnet/marshal-context-class.md)