---
title: Información general de la serialización en C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1f950c8efbdd75e16096d158075e92594fb6b2d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-marshaling-in-c"></a>Información general de la serialización en C++
En modo mixto, deben serializar los datos entre los tipos nativos y los administrados. [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] introdujo la biblioteca de cálculo de referencias para ayudarle a calcular y convertir los datos de una manera sencilla.  
  
 También puede usar la biblioteca de serialización con o sin un [marshal_context (clase)](../dotnet/marshal-context-class.md). Algunas conversiones requieren un contexto. Otras conversiones pueden implementarse utilizando la [marshal_as](../dotnet/marshal-as.md) función. En la tabla siguiente se enumeran las conversiones actuales compatibles y se indica si requieren un contexto y el archivo de serializar que se debe incluir:  
  
|De tipo|A tipo|Método serializar|Incluir archivo|  
|---------------|-------------|--------------------|------------------|  
|System::String^|const char *|marshal_context|serializar.h|  
|const char *|System::String^|serializar_as|serializar.h|  
|char*|System::String^|serializar_as|serializar.h|  
|System::String^|const wchar_t*|serializar_context|marshal.h|  
|const wchar_t *|System::String^|serializar_as|serializar.h|  
|wchar_t*|System::String^|serializar_as|serializar.h|  
|System::IntPtr|HANDLE|serializar_as|serializar_windows.h|  
|HANDLE|System::IntPtr|serializar_as|serializar_windows.h|  
|System::String^|BSTR|serializar_context|serializar_windows.h|  
|BSTR|System::String^|serializar_as|serializar.h|  
|System::String^|bstr_t|serializar_as|marshal_windows.h|  
|bstr_t|System::String^|serializar_as|serializar_windows.h|  
|System::String^|std::string|marshal_as|serializar_cppstd.h|  
|std::string|System::String^|serializar_as|serializar_cppstd.h|  
|System::String^|std::wstring|serializar_as|marshal_cppstd.h|  
|std::wstring|System::String^|serializar_as|serializar_cppstd.h|  
|System::String^|CStringT\<char >|serializar_as|serializar_atl.h|  
|CStringT\<char >|System::String^|serializar_as|serializar_atl.h|  
|System::String^|CStringT<wchar_t>|serializar_as|serializar_atl.h|  
|CStringT<wchar_t>|System::String^|serializar_as|serializar_atl.h|  
|System::String^|CComBSTR|serializar_as|serializar_atl.h|  
|CComBSTR|System::String^|serializar_as|serializar_atl.h|  
  
 El cálculo de referencias requiere un contexto solo cuando se calcula de tipos de datos administrados a tipos de datos nativos y el tipo nativo que se va a convertir no tiene un destructor para la limpieza automática. El contexto de cálculo de referencias destruye el tipo de datos nativo asignado en su destructor. Por consiguiente, las conversiones que requieren un contexto serán válidas solo hasta que se elimine el contexto. Para guardar cualquier valor de cálculo de referencias, debe copiar los valores a sus propias variables.  
  
> [!NOTE]
>  Si ha incrustado valores `NULL`en la cadena, el resultado de calcular la cadena no se puede garantizar. Los valores `NULL` incrustados pueden hacer que la cadena se trunque o no pueda conservarse.  
  
 Los encabezados de la biblioteca de cálculo de referencias se encuentran en el directorio de inclusión en el subdirectorio msclr. Este ejemplo muestra cómo incluir el directorio msclr en una declaración de encabezado de inclusión:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 La biblioteca de cálculo de referencias es extensible para que pueda agregar sus propios tipos de serialización. Para obtener más información sobre cómo extender la biblioteca de serialización, vea [Cómo: Extender la biblioteca de cálculo de referencias](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 En versiones anteriores, se podían serializar los datos mediante el uso de [de invocación de plataforma](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Para obtener más información acerca de `PInvoke`, consulte [llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de compatibilidad de C++](../dotnet/cpp-support-library.md)   
 [Cómo: Extender la biblioteca de serialización](../dotnet/how-to-extend-the-marshaling-library.md)