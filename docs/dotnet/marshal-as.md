---
title: "marshal_as | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_as"
  - "msclr.interop.marshal_as"
  - "msclr::interop::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_as (plantilla) [C++]"
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este método convierte los datos entre los entornos nativo y administrado.  
  
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
 Este método es una manera simplificada de convertir datos entre los tipos nativos y administrados.  Para determinar qué tipos de datos se admiten, vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md).  Algunas conversiones de datos requieren un contexto.  Puede convertir los tipos de datos mediante [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md).  
  
 Si intenta calcular las referencias de un par de tipos de datos que no se admiten, `marshal_as` generará un error [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) en tiempo de compilación.  Lea el mensaje proporcionado con el error para obtener más información.  El error `C4996` se puede generar para algunas funciones, aparte de las desusadas.  Un ejemplo de esto consiste en intentar para calcular las referencias de un par de tipos de datos que no se admiten.  
  
 La biblioteca de cálculo de referencias se compone de varios archivos de encabezado.  Cualquier conversión requiere solo un archivo, pero puede incluir archivos adicionales si los necesita para otras conversiones.  Para ver qué conversiones están asociadas con qué archivos, consulte la tabla de `Marshaling Overview`.  Independientemente de la conversión que desee hacer, el requisito de espacio de nombres siempre está en vigor.  
  
## Ejemplo  
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
  
## Requisitos  
 **Archivo de encabezado:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, o \<msclr\\marshal\_atl.h\>  
  
 **Espacio de nombres:** msclr::interop  
  
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md)