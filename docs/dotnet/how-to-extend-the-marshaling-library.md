---
title: 'Cómo: Extender la biblioteca de cálculo de referencias'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: ab3b17638e07a54189803c83163db67c5ebf82a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545274"
---
# <a name="how-to-extend-the-marshaling-library"></a>Cómo: Extender la biblioteca de cálculo de referencias

En este tema se explica cómo extender la biblioteca de serialización para proporcionar más conversiones entre los tipos de datos. Los usuarios pueden extender la biblioteca de serialización para las conversiones de datos que no admite actualmente la biblioteca.

Puede extender la biblioteca de serialización de una de las dos maneras siguientes: con o sin una [clase marshal_context](../dotnet/marshal-context-class.md). Revise la [información general sobre el cálculo C++ de referencias en](../dotnet/overview-of-marshaling-in-cpp.md) el tema para determinar si una nueva conversión requiere un contexto.

En ambos casos, primero se crea un archivo para las nuevas conversiones de cálculo de referencias. Lo hace para conservar la integridad de los archivos de la biblioteca de serialización estándar. Si desea trasladar un proyecto a otro equipo o a otro programador, debe copiar el nuevo archivo de serialización junto con el resto del proyecto. De esta manera, se garantizará que el usuario que recibe el proyecto recibirá las conversiones nuevas y no tendrá que modificar ningún archivo de biblioteca.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Para extender la biblioteca de serialización con una conversión que no requiere un contexto

1. Cree un archivo para almacenar las nuevas funciones de cálculo de referencias, por ejemplo, Marshal. h.

1. Incluya uno o más de los archivos de biblioteca de serialización:

   - Marshal. h para tipos base.

   - marshal_windows. h para tipos de datos de Windows.

   - marshal_cppstd. h para C++ tipos de datos de la biblioteca estándar.

   - marshal_atl. h para tipos de datos de ATL.

1. Utilice el código al final de estos pasos para escribir la función de conversión. En este código, para es el tipo al que se va a convertir, de es el tipo del que se va a convertir y `from` es el parámetro que se va a convertir.

1. Reemplace el comentario sobre la lógica de conversión por código para convertir el parámetro `from` en un objeto de para escribir y devolver el objeto convertido.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Para extender la biblioteca de serialización con una conversión que requiere un contexto

1. Cree un archivo para almacenar las nuevas funciones de cálculo de referencias, por ejemplo, Marshal. h

1. Incluya uno o más de los archivos de biblioteca de serialización:

   - Marshal. h para tipos base.

   - marshal_windows. h para tipos de datos de Windows.

   - marshal_cppstd. h para C++ tipos de datos de la biblioteca estándar.

   - marshal_atl. h para tipos de datos de ATL.

1. Utilice el código al final de estos pasos para escribir la función de conversión. En este código, para es el tipo al que se va a convertir, de es el tipo del que se va a convertir, `toObject` es un puntero en el que se va a almacenar el resultado y `fromObject` es el parámetro que se va a convertir.

1. Reemplace el comentario sobre la inicialización con código para inicializar el `toPtr` en el valor vacío adecuado. Por ejemplo, si es un puntero, establézcalo en `NULL`.

1. Reemplace el comentario sobre la lógica de conversión por código para convertir el parámetro `from` en un objeto de *a* tipo. Este objeto convertido se almacenará en `toPtr`.

1. Reemplace el comentario sobre el establecimiento de `toObject` por el código para establecer `toObject` en el objeto convertido.

1. Reemplace el comentario sobre la limpieza de recursos nativos con código para liberar cualquier memoria asignada por `toPtr`. Si `toPtr` memoria asignada mediante `new`, utilice `delete` para liberar memoria.

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

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se extiende la biblioteca de serialización con una conversión que no requiere un contexto. En este ejemplo, el código convierte la información de empleado de un tipo de datos nativo a un tipo de datos administrado.

```cpp
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

En el ejemplo anterior, la función `marshal_as` devuelve un identificador a los datos convertidos. Esto se hizo para evitar la creación de una copia adicional de los datos. La devolución directa de la variable tendría un costo de rendimiento innecesario asociado.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se convierte la información de empleado de un tipo de datos administrado a un tipo de datos nativo. Esta conversión requiere un contexto de serialización.

```cpp
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

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>Consulte también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)
