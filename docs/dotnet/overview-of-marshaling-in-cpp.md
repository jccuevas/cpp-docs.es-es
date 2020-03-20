---
title: Información general de la serialización en C++
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 937fbdf4b3ed09344e69a8f1eb731565c36794ae
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544439"
---
# <a name="overview-of-marshaling-in-ccli"></a>Información general sobre el cálculo C++de referencias en/CLI

En modo mixto, deben serializar los datos entre los tipos nativos y los administrados. La *biblioteca de cálculo de referencias* le ayuda a calcular las referencias y convertir los datos de una manera sencilla.  La biblioteca de serialización se compone de un conjunto de funciones y una `marshal_context` clase que realiza el cálculo de referencias para tipos comunes. La biblioteca se define en estos encabezados en el directorio **include/msclr** de la edición de Visual Studio:

|Encabezado|Descripción|
|---------------|-----------------|
|serializar.h|clases de `marshal_context` y funciones de serialización sin contexto|
|serializar_atl.h| Funciones para calcular las referencias de tipos ATL|
|serializar_cppstd.h|Funciones para calcular las referencias C++ de tipos estándar|
|marshal_windows.h|Funciones para calcular las referencias de tipos de Windows|

La ruta de acceso predeterminada de la carpeta **msclr** es similar a la de la edición que tiene y el número de compilación:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Puede usar la biblioteca de cálculo de referencias con o sin una [clase marshal_context](../dotnet/marshal-context-class.md). Algunas conversiones requieren un contexto. Se pueden implementar otras conversiones mediante la función [marshal_as](../dotnet/marshal-as.md) . En la tabla siguiente se enumeran las conversiones actuales compatibles y se indica si requieren un contexto y el archivo de serializar que se debe incluir:

|De tipo|A tipo|Método serializar|Incluir archivo|
|---------------|-------------|--------------------|------------------|
|System::String^|const char \*|serializar_context|serializar.h|
|const char \*|System::String^|serializar_as|serializar.h|
|char \*|System::String^|serializar_as|serializar.h|
|System::String^|wchar_t const\*|serializar_context|serializar.h|
|wchar_t const \*|System::String^|serializar_as|serializar.h|
|wchar_t \*|System::String^|serializar_as|serializar.h|
|System::IntPtr|HANDLE|serializar_as|marshal_windows.h|
|HANDLE|System::IntPtr|serializar_as|marshal_windows.h|
|System::String^|BSTR|serializar_context|marshal_windows.h|
|BSTR|System::String^|serializar_as|serializar.h|
|System::String^|bstr_t|serializar_as|marshal_windows.h|
|bstr_t|System::String^|serializar_as|marshal_windows.h|
|System::String^|std::string|serializar_as|serializar_cppstd.h|
|std::string|System::String^|serializar_as|serializar_cppstd.h|
|System::String^|std::wstring|serializar_as|serializar_cppstd.h|
|std::wstring|System::String^|serializar_as|serializar_cppstd.h|
|System::String^|CStringT\<> Char|serializar_as|serializar_atl.h|
|CStringT\<> Char|System::String^|serializar_as|serializar_atl.h|
|System::String^|CStringT<wchar_t>|serializar_as|serializar_atl.h|
|CStringT<wchar_t>|System::String^|serializar_as|serializar_atl.h|
|System::String^|CComBSTR|serializar_as|serializar_atl.h|
|CComBSTR|System::String^|serializar_as|serializar_atl.h|

El cálculo de referencias requiere un contexto solo cuando se calcula de tipos de datos administrados a tipos de datos nativos y el tipo nativo que se va a convertir no tiene un destructor para la limpieza automática. El contexto de serialización destruye el tipo de datos nativo asignado en su destructor. Por consiguiente, las conversiones que requieren un contexto serán válidas solo hasta que se elimine el contexto. Para guardar cualquier valor de cálculo de referencias, debe copiar los valores a sus propias variables.

> [!NOTE]
>  Si ha incrustado valores `NULL`en la cadena, el resultado de serializar la cadena no se puede garantizar. Los valores `NULL` incrustados pueden hacer que la cadena se trunque o no pueda conservarse.

Este ejemplo muestra cómo incluir el directorio msclr en una declaración de encabezado de inclusión:

`#include "msclr\marshal_cppstd.h"`

La biblioteca de cálculo de referencias es extensible para que pueda agregar sus propios tipos de serialización. Para obtener más información sobre cómo extender la biblioteca de cálculo de referencias, vea [Cómo: extender la biblioteca de serialización](../dotnet/how-to-extend-the-marshaling-library.md).

## <a name="see-also"></a>Consulte también

[Biblioteca de compatibilidad de C++](../dotnet/cpp-support-library.md)<br/>
[Cómo: Extender la biblioteca de serialización](../dotnet/how-to-extend-the-marshaling-library.md)
