---
title: Integración de WRL (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2fc36582e6ffbff8f7608a5a26cc472687132e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760983"
---
# <a name="wrl-integration-ccx"></a>Integración de WRL (C++/CX)

Puede mezclar libremente código WRL con código de biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución. En la misma unidad de traducción puedes usar objetos declarados con el identificador al objeto WRL (`^`) puntero inteligente de notación y WRL (`ComPtr<T>`) notación. Sin embargo, debe controlar manualmente los valores devueltos y los códigos de error de WRL HRESULT y excepciones de WRL.
  
## <a name="wrl-development"></a>Desarrollo de WRL

Para obtener más información sobre la creación y consumo de componentes WRL, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Ejemplo

El fragmento de código siguiente se muestra mediante WRL y WRL para consumir las clases en tiempo de ejecución de Windows y examinar un archivo de metadatos.

El ejemplo está tomado de un fragmento de código en el foro de aplicaciones de creación de Microsoft Store. El autor de este fragmento de código proporciona los avisos de declinación de responsabilidades y las estipulaciones siguientes:

1. C++ no proporciona API específicas para reflejarse en los tipos en tiempo de ejecución de Windows, pero los archivos de metadatos de Windows (.winmd) para un tipo son totalmente compatibles con los archivos de metadatos CLR. Windows proporciona las nuevas API de detección de metadatos (RoGetMetaDataFile) para obtener el archivo .winmd para un tipo determinado. Sin embargo, estas API son de uso limitado para los programadores de C++ porque no puedes crear instancias de una clase.

1. Una vez compilado el código, también necesitarás pasar Runtimeobject.lib y Rometadata.lib al vinculador.

1. Este fragmento de código se muestra tal cual. Aunque se espera que funcione correctamente, es posible que contenga errores.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}

```

## <a name="see-also"></a>Vea también

[Interoperar con otros lenguajes](interoperating-with-other-languages-c-cx.md)  
