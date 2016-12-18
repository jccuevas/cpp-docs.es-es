---
title: "Informaci&#243;n general del c&#225;lculo de referencias en C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshaling"
  - "marshalling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Biblioteca de compatibilidad de C++, calcular las referencias"
  - "calcular las referencias, acerca del cálculo de referencias"
  - "Visual C++, calcular las referencias"
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general del c&#225;lculo de referencias en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En modo mixto, deben calcularse a veces las referencias de los datos entre los tipos nativos y los administrados.  [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] introdujo la biblioteca de cálculo de referencias para ayudarle a calcular y convertir los datos de una manera sencilla.  
  
 Puede utilizar la biblioteca de cálculo de referencias con o sin una [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md).  Algunas conversiones requieren un contexto.  Otras conversiones se pueden implementar mediante la función [marshal\_as](../dotnet/marshal-as.md).  En la tabla siguiente se enumeran las conversiones actuales compatibles y se indica si requieren un contexto y el archivo de cálculo de referencias que se debe incluir:  
  
|De tipo|A tipo|Método de cálculo de referencias|Incluir archivo|  
|-------------|------------|--------------------------------------|---------------------|  
|System::String^|const char \*|marshal\_context|marshal.h|  
|const char \*|System::String^|marshal\_as|marshal.h|  
|char\*|System::String^|marshal\_as|marshal.h|  
|System::String^|const wchar\_t\*|marshal\_context|marshal.h|  
|const wchar\_t \*|System::String^|marshal\_as|marshal.h|  
|wchar\_t\*|System::String^|marshal\_as|marshal.h|  
|System::IntPtr|HANDLE|marshal\_as|marshal\_windows.h|  
|HANDLE|System::IntPtr|marshal\_as|marshal\_windows.h|  
|System::String^|BSTR|marshal\_context|marshal\_windows.h|  
|BSTR|System::String^|marshal\_as|marshal.h|  
|System::String^|bstr\_t|marshal\_as|marshal\_windows.h|  
|bstr\_t|System::String^|marshal\_as|marshal\_windows.h|  
|System::String^|std::string|marshal\_as|marshal\_cppstd.h|  
|std::string|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|std::wstring|marshal\_as|marshal\_cppstd.h|  
|std::wstring|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|CStringT\<char\>|marshal\_as|marshal\_atl.h|  
|CStringT\<char\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CStringT\<wchar\_t\>|marshal\_as|marshal\_atl.h|  
|CStringT\<wchar\_t\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CComBSTR|marshal\_as|marshal\_atl.h|  
|CComBSTR|System::String^|marshal\_as|marshal\_atl.h|  
  
 El cálculo de referencias requiere un contexto solo cuando se calcula de tipos de datos administrados a tipos de datos nativos y el tipo nativo que se va a convertir no tiene un destructor para la limpieza automática.  El contexto de cálculo de referencias destruye el tipo de datos nativo asignado en su destructor.  Por consiguiente, las conversiones que requieren un contexto serán válidas solo hasta que se elimine el contexto.  Para guardar cualquier valor de cálculo de referencias, debe copiar los valores a sus propias variables.  
  
> [!NOTE]
>  Si ha incrustado valores `NULL`en la cadena, el resultado de calcular la cadena no se puede garantizar.  Los valores `NULL` incrustados pueden hacer que la cadena se trunque o no pueda conservarse.  
  
 Los encabezados de la biblioteca de cálculo de referencias se encuentran en el directorio de inclusión en el subdirectorio msclr.  Este ejemplo muestra cómo incluir el directorio msclr en una declaración de encabezado de inclusión:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 La biblioteca de cálculo de referencias es extensible para que pueda agregar sus propios tipos de cálculo de referencias.  Para obtener más información sobre cómo extender la biblioteca de cálculo de referencias, vea [Cómo: Extender la biblioteca de cálculo de referencias](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 En versiones anteriores, se podían calcular las referencias de los datos mediante [Invocación de plataforma](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md).  Para obtener más información sobre `PInvoke`, vea [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md).  
  
## Vea también  
 [Biblioteca de compatibilidad de C\+\+](../dotnet/cpp-support-library.md)   
 [Cómo: Extender la biblioteca de cálculo de referencias](../dotnet/how-to-extend-the-marshaling-library.md)