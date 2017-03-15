---
title: "marshal_context::marshal_as | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_context::marshal_as"
  - "marshal_context.marshal_as"
  - "msclr.interop.marshal_context.marshal_as"
  - "msclr::interop::marshal_context::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context (clase) [C++], operaciones"
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# marshal_context::marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Realiza el cálculo en un objeto de datos específico para convertirlo entre un tipo de datos administrado y nativo.  
  
## Sintaxis  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### Parámetros  
 \[in\] `input`  
 El valor cuyas referencias desea calcular para una variable `To_Type`.  
  
## Valor devuelto  
 Una variable de tipo `To_Type` que es el valor convertido de `input`.  
  
## Comentarios  
 Esta función realiza el cálculo en un objeto de datos específico.  Utilice esta función únicamente con las conversiones indican en la tabla en [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Si intenta calcular las referencias de un par de tipos de datos que no se admiten, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación.  Lea el mensaje proporcionado con el error para obtener más información.  El error `C4996` se puede generar para algunas funciones, aparte de las desusadas.  Dos condiciones que generarán este error intenten para formar un par de tipos de datos que no son compatibles y se intenta utilizar `marshal_as` para una conversión que requiere un contexto.  
  
 La biblioteca de cálculo de referencias se compone de varios archivos de encabezado.  Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones.  La tabla en `Marshaling Overview in C++` indica qué archivo de cálculo debe incluirse para cada conversión.  
  
## Ejemplo  
 Este ejemplo crea un contexto para calcular las referencias de `System::String` a un tipo de variable de `const char *` .  Los datos convertidos no serán válidos después de la línea que elimina el contexto.  
  
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
  
## Requisitos  
 **Archivo de encabezado:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, o \<msclr\\marshal\_atl.h\>  
  
 **Espacio de nombres:** msclr::interop  
  
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md)