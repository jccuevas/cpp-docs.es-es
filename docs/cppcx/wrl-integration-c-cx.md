---
title: "Integración de WRL (C++ / CX) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 234141df693f67b97bf2ec83bd9063f69addeb0f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="wrl-integration-ccx"></a>Integración de WRL (C++/CX)

Puede mezclar libremente código WRL con [!INCLUDE[cppwrl](includes/cppwrl-md.md)] ([!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]) código. En la misma unidad de traducción, puede usar objetos declarados con identificador a objeto WRL (`^`) notación y [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] puntero inteligente (`ComPtr<T>`) notación. Sin embargo, debes controlar manualmente los valores devueltos, y [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] HRESULT códigos de error y las excepciones de WRL.
  
## <a name="includecppwrlshortincludescppwrl-short-mdmd-development"></a>Desarrollo de[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] 

Para obtener más información acerca de la creación y el consumo [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] de componentes, vea [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Ejemplo

El fragmento de código siguiente se muestra el uso de WRL y [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] para consumir [!INCLUDE[wrt](includes/wrt-md.md)] clases y examinar un archivo de metadatos.

El ejemplo está tomado de un fragmento de código en el foro de aplicaciones de almacén de Microsoft de creación. El autor de este fragmento de código proporciona los avisos de declinación de responsabilidades y las estipulaciones siguientes:

1. C++ no proporciona API específicas para aplicar reflexión en tipos de [!INCLUDE[wrt](includes/wrt-md.md)] , pero los archivos de metadatos de Windows (.winmd) para un tipo son totalmente conformes a los archivos de metadatos CLR. Windows proporciona las nuevas API de detección de metadatos (RoGetMetaDataFile) para obtener el archivo .winmd para un tipo determinado. Sin embargo, estas API son de uso limitado para los programadores de C++ porque no puedes crear instancias de una clase.

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
