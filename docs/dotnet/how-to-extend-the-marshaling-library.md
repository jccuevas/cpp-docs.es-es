---
title: 'Cómo: Extender la biblioteca de serialización'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 697a246012544e6be1189b6cc40d6185e5ec26d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569859"
---
# <a name="how-to-extend-the-marshaling-library"></a>Cómo: Extender la biblioteca de serialización

En este tema se explica cómo extender la biblioteca de serialización para proporcionar más conversiones entre tipos de datos. Los usuarios pueden extender la biblioteca de serialización para cualquier conversión de datos que no se admite actualmente por la biblioteca.

Puede extender la biblioteca de cálculo de referencias en uno de dos maneras: con o sin un [marshal_context Class](../dotnet/marshal-context-class.md). Revise el [Overview of Marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) tema para determinar si una nueva conversión requiere un contexto.

En ambos casos, en primer lugar cree un archivo para nuevas conversiones de cálculo de referencias. Hacerlo para mantener la integridad del cálculo de referencias de archivos de la biblioteca estándar. Si desea trasladar un proyecto a otro equipo o a otro programador, debe copiar el archivo nuevo cálculo de referencias junto con el resto del proyecto. De esta manera, el usuario que recibe el proyecto tendrá la garantía de recibir las nuevas conversiones y no tendrá que modificar los archivos de biblioteca.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Para extender la biblioteca de cálculo de referencias con una conversión que no requiere un contexto

1. Cree un archivo para almacenar las nuevas funciones de cálculo de referencias;.

1. Incluir uno o varios de los archivos de biblioteca de cálculo de referencias:

   - Marshal.h para los tipos base.

   - marshal_windows.h para tipos de datos de windows.

   - marshal_cppstd.h para tipos de datos de la biblioteca estándar de C++.

   - marshal_atl.h para tipos de datos ATL.

1. Use el código al final de estos pasos para escribir la función de conversión. En este código, que es el tipo para convertir en, FROM es el tipo para convertir de, y `from` es el parámetro que se va a convertir.

1. Reemplace el comentario sobre la lógica de conversión con el código para convertir el `from` parámetro en un objeto de para escribir y devolver el objeto convertido.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Para extender la biblioteca con una conversión que requiere un contexto de serialización

1. Crear un archivo para almacenar las nuevas funciones de cálculo de referencias

1. Incluir uno o varios de los archivos de biblioteca de cálculo de referencias:

   - Marshal.h para los tipos base.

   - marshal_windows.h para tipos de datos de windows.

   - marshal_cppstd.h para tipos de datos de la biblioteca estándar de C++.

   - marshal_atl.h para tipos de datos ATL.

1. Use el código al final de estos pasos para escribir la función de conversión. En este código, que es el tipo para convertir en, FROM es el tipo de conversión, `toObject` es un puntero en el que se va a almacenar el resultado, y `fromObject` es el parámetro que se va a convertir.

1. Reemplace el comentario sobre la inicialización con código para inicializar el `toPtr` al valor vacío adecuado. Por ejemplo, si es un puntero, establézcalo en `NULL`.

1. Reemplace el comentario sobre la lógica de conversión con el código para convertir el `from` parámetro en un objeto de *TO* tipo. Este objeto convertido se almacenará en `toPtr`.

1. Reemplace el comentario sobre la configuración de `toObject` con el código para establecer `toObject` en el objeto convertido.

1. Reemplace el comentario sobre la liberación de recursos nativos con código para liberar memoria asignada por `toPtr`. Si `toPtr` memoria asignada mediante el uso de `new`, utilice `delete` para liberar la memoria.

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

El ejemplo siguiente amplía con una conversión que no requiere un contexto de la biblioteca de serialización. En este ejemplo, el código convierte la información del empleado de un tipo de datos nativo a un tipo de datos administrados.

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

En el ejemplo anterior, el `marshal_as` función devuelve un identificador para los datos convertidos. Esto se hace para evitar la creación de una copia adicional de los datos. Devolver directamente la variable habría un costo de rendimiento innecesaria asociados con él.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se convierte la información del empleado de un tipo de datos administrado a un tipo de datos nativos. Esta conversión requiere un contexto de cálculo de referencias.

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

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>Vea también

[Información general de la serialización en C++](../dotnet/overview-of-marshaling-in-cpp.md)