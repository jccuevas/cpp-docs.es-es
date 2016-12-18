---
title: "C&#243;mo: Extender la biblioteca de c&#225;lculo de referencias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "biblioteca de cálculo de referencias, extender"
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Extender la biblioteca de c&#225;lculo de referencias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se explica cómo extender la biblioteca de cálculo de referencias para proporcionar más conversiones entre los tipos de datos.  Los usuarios pueden extender la biblioteca de cálculo de referencias para cualquier conversión de datos no admitida actualmente por la biblioteca.  
  
 Puede extender la biblioteca de cálculo de referencias de una de estas dos formas: con o sin [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md).  Revise el tema [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md) para determinar si una nueva conversión requiere un contexto.  
  
 En ambos casos, cree primero un archivo para las nuevas conversiones de cálculo de referencias.  Esto se hace para conservar la integridad de los archivos de la biblioteca de cálculo de referencias estándar.  Si desea trasladar un proyecto a otro equipo o a otro programador, debe copiar el nuevo archivo de cálculo de referencias junto con el resto del proyecto.  De esta manera, el usuario que recibe el proyecto tendrá la garantía de recibir las nuevas conversiones y no tendrá que modificar ningún archivo de biblioteca.  
  
### Para Extender la biblioteca de cálculo de referencias con una conversión que no requiere un contexto  
  
1.  Cree un archivo para almacenar las nuevas funciones de cálculo de referencias, por ejemplo, MyMarshal.h.  
  
2.  Incluya uno o varios archivos de la biblioteca de cálculo de referencias:  
  
    -   marshal.h para los tipos base.  
  
    -   marshal\_windows.h para tipos de datos de ventanas.  
  
    -   marshal\_cppstd.h para tipos de datos de STL.  
  
    -   marshal\_atl.h para tipos de datos de ATL.  
  
3.  Utilice el código que se muestra al final de estos pasos para escribir la función de conversión.  En este código, TO es el tipo al que se convierte, FROM es el tipo desde el que se convierte, y `from` es el parámetro que se va a convertir.  
  
4.  Reemplace el comentario sobre la lógica de la conversión con código para convertir el parámetro `from` en un objeto de tipo TO y devuelva el objeto convertido.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      inline TO marshal_as<TO, FROM> (const FROM& from) {  
         // Insert conversion logic here, and return a TO parameter.  
      }  
   }  
}  
```  
  
### Para extender la biblioteca de cálculo de referencias con una conversión que requiere un contexto  
  
1.  Cree un archivo para almacenar las nuevas funciones de cálculo de referencias; por ejemplo, MyMarshal.h  
  
2.  Incluya uno o varios archivos de la biblioteca de cálculo de referencias:  
  
    -   marshal.h para los tipos base.  
  
    -   marshal\_windows.h para tipos de datos de ventanas.  
  
    -   marshal\_cppstd.h para tipos de datos de STL.  
  
    -   marshal\_atl.h para tipos de datos de ATL.  
  
3.  Utilice el código que se muestra al final de estos pasos para escribir la función de conversión.  En este código, TO es el tipo al que se convierte, FROM es el tipo desde el que se convierte, `toObject` es un puntero en el que se almacena el resultado, y `fromObject` es el parámetro que se va a convertir.  
  
4.  Reemplace el comentario sobre la inicialización con código para inicializar `toPtr` con el valor vacío adecuado.  Por ejemplo, si es un puntero, establézcalo en `NULL`.  
  
5.  Reemplace el comentario sobre la lógica de conversión con código para convertir el parámetro de `from` en un objeto de tipo de *TO* .  Este objeto convertido se almacenará en `toPtr`.  
  
6.  Reemplace el comentario sobre cómo configurar `toObject` con código para establecer `toObject` en el objeto convertido.  
  
7.  Reemplace el comentario sobre cómo limpiar los recursos nativos con código para liberar la memoria asignada por `toPtr`.  Si `toPtr` asignó memoria mediante `new`, utilice `delete` para liberar la memoria.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<TO, FROM> : public context_node_base  
      {  
      private:  
         TO toPtr;  
      public:  
         context_node(TO& toObject, FROM fromObject)  
         {  
            // (Step 4) Initialize toPtr to the appropriate empty value.  
            // (Step 5) Insert conversion logic here.  
            // (Step 6) Set toObject to the converted parameter.  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // (Step 7) Clean up native resources.  
         }  
      };  
   }  
}   
```  
  
## Ejemplo  
 El ejemplo siguiente extiende la biblioteca de cálculo de referencias con una conversión que no requiere un contexto.  En este ejemplo, el código convierte la información de empleado \(employee\) desde un tipo de datos nativo a un tipo de datos administrados.  
  
```  
// MyMarshalNoContext.cpp  
// compile with: /clr  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   char* name;  
   char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {  
         ManagedEmp^ toValue = gcnew ManagedEmp;  
         toValue->name = marshal_as<System::String^>(from.name);  
         toValue->address = marshal_as<System::String^>(from.address);  
         toValue->zipCode = from.zipCode;  
         return toValue;  
      }  
   }  
}  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {   
   NativeEmp employee;  
  
   employee.name = "Jeff Smith";  
   employee.address = "123 Main Street";  
   employee.zipCode = 98111;  
  
   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);  
  
   Console::WriteLine("Managed name: {0}", result->name);  
   Console::WriteLine("Managed address: {0}", result->address);  
   Console::WriteLine("Managed zip code: {0}", result->zipCode);  
  
   return 0;  
}  
```  
  
 En el ejemplo anterior, la función `marshal_as` devuelve un identificador a los datos convertidos.  Esto se ha hecho así para evitar la creación de una copia adicional de los datos.  Devolver directamente la variable hubiera tenido un coste de rendimiento innecesario.  
  
  **Nombre administrado: Jeff Smith**  
**Dirección administrada: 123 Main Street**  
**Código postal administrado: 98111**   
## Ejemplo  
 El siguiente ejemplo convierte la información de empleado desde un tipo de datos administrados a un tipo de datos nativos.  Esta conversión requiere un contexto de cálculo de referencias.  
  
```  
// MyMarshalContext.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   const char* name;  
   const char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base  
      {  
      private:  
         NativeEmp* toPtr;  
         marshal_context context;  
      public:  
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)  
         {  
            // Conversion logic starts here  
            toPtr = NULL;  
  
            const char* nativeName;  
            const char* nativeAddress;  
  
            // Convert the name from String^ to const char*.  
            System::String^ tempValue = fromObject->name;  
            nativeName = context.marshal_as<const char*>(tempValue);  
  
            // Convert the address from String^ to const char*.  
            tempValue = fromObject->address;  
            nativeAddress = context.marshal_as<const char*>(tempValue);  
  
            toPtr = new NativeEmp();  
            toPtr->name = nativeName;  
            toPtr->address = nativeAddress;  
            toPtr->zipCode = fromObject->zipCode;  
  
            toObject = toPtr;  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // When the context is deleted, it will free the memory  
            // allocated for toPtr->name and toPtr->address, so toPtr  
            // is the only memory that needs to be freed.  
            if (toPtr != NULL) {  
               delete toPtr;  
               toPtr = NULL;  
            }  
         }  
      };  
   }  
}   
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   ManagedEmp^ employee = gcnew ManagedEmp();  
  
   employee->name = gcnew String("Jeff Smith");  
   employee->address = gcnew String("123 Main Street");  
   employee->zipCode = 98111;  
  
   marshal_context context;  
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);  
  
   if (result != NULL) {  
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",  
         result->name, result->address, result->zipCode);  
   }  
  
   return 0;  
}  
```  
  
  **Nombre nativo: Jeff Smith**  
**Dirección nativa: 123 Main Street**  
**Código postal nativo: 98111**   
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)