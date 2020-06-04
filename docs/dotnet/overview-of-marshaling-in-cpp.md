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
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372009"
---
# <a name="overview-of-marshaling-in-ccli"></a>Resumen del cálculo de referencias en C++/CLI

En modo mixto, deben serializar los datos entre los tipos nativos y los administrados. La *biblioteca de cálculo* de referencias le ayuda a calcular las referencias y convertir datos de una manera sencilla.  La biblioteca de cálculo de referencias `marshal_context` consta de un conjunto de funciones y una clase que realizan el cálculo de referencias para tipos comunes. La biblioteca se define en estos encabezados en el directorio **include/msclr** de la edición de Visual Studio:

|Encabezado|Descripción|
|---------------|-----------------|
|serializar.h|`marshal_context`clase y funciones de cálculo de referencias sin contexto|
|serializar_atl.h| Funciones para serializar tipos ATL|
|serializar_cppstd.h|Funciones para serializar tipos C++ estándar|
|marshal_windows.h|Funciones para calcular el cálculo de referencias de tipos de Windows|

La ruta predeterminada para la carpeta **msclr** es algo así dependiendo de la edición que tenga y el número de compilación:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Puede utilizar la biblioteca de cálculo de referencias con o sin una [clase de marshal_context](../dotnet/marshal-context-class.md). Algunas conversiones requieren un contexto. Otras conversiones se pueden implementar mediante la función [marshal_as.](../dotnet/marshal-as.md) En la tabla siguiente se enumeran las conversiones actuales compatibles y se indica si requieren un contexto y el archivo de serializar que se debe incluir:

|De tipo|A tipo|Método serializar|Incluir archivo|
|---------------|-------------|--------------------|------------------|
|System::String^|const char\*|serializar_context|serializar.h|
|const char\*|System::String^|serializar_as|serializar.h|
|Char\*|System::String^|serializar_as|serializar.h|
|System::String^|const wchar_t\*|serializar_context|serializar.h|
|const wchar_t \*|System::String^|serializar_as|serializar.h|
|Wchar_t\*|System::String^|serializar_as|serializar.h|
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
|System::String^|CStringT\<char>|serializar_as|serializar_atl.h|
|CStringT\<char>|System::String^|serializar_as|serializar_atl.h|
|System::String^|CStringT<wchar_t<>|serializar_as|serializar_atl.h|
|CStringT<wchar_t<>|System::String^|serializar_as|serializar_atl.h|
|System::String^|CComBSTR|serializar_as|serializar_atl.h|
|CComBSTR|System::String^|serializar_as|serializar_atl.h|

El cálculo de referencias requiere un contexto solo cuando se calcula de tipos de datos administrados a tipos de datos nativos y el tipo nativo que se va a convertir no tiene un destructor para la limpieza automática. El contexto de serialización destruye el tipo de datos nativo asignado en su destructor. Por consiguiente, las conversiones que requieren un contexto serán válidas solo hasta que se elimine el contexto. Para guardar cualquier valor de cálculo de referencias, debe copiar los valores a sus propias variables.

> [!NOTE]
> Si ha incrustado valores `NULL`en la cadena, el resultado de serializar la cadena no se puede garantizar. Los valores `NULL` incrustados pueden hacer que la cadena se trunque o no pueda conservarse.

Este ejemplo muestra cómo incluir el directorio msclr en una declaración de encabezado de inclusión:

`#include "msclr\marshal_cppstd.h"`

La biblioteca de cálculo de referencias es extensible para que pueda agregar sus propios tipos de serialización. Para obtener más información acerca de cómo ampliar la biblioteca de cálculo de referencias, vea [Cómo: extender la](../dotnet/how-to-extend-the-marshaling-library.md)biblioteca de cálculo de referencias .

## <a name="see-also"></a>Consulte también

[Biblioteca de compatibilidad de C++](../dotnet/cpp-support-library.md)<br/>
[Cómo: Extender la biblioteca de cálculo de referencias](../dotnet/how-to-extend-the-marshaling-library.md)
