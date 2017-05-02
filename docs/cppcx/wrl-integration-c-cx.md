---
title: "Integraci&#243;n de WRL (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Integraci&#243;n de WRL (C++/CX)
Puedes mezclar libremente código de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] con código de [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)] \([!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)]\). En la misma unidad de traducción puedes usar objetos declarados con la notación \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) de tipo "indicador a objeto" de `^` y la notación \([!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)]\) de puntero inteligente de `ComPtr<T>`. Sin embargo, debes controlar manualmente los valores devueltos, los códigos de error HRESULT de [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] y las excepciones de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)].  
  
## Desarrollo de [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)]  
 Para obtener más información sobre la creación y la utilización de componentes de [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)], consulta [Biblioteca de plantillas de Windows Runtime C\+\+ \(WRL\)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
## Ejemplo  
 En el siguiente fragmento de código se muestra el uso de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] y [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] para utilizar clases de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y examinar un archivo de metadatos.  
  
 El ejemplo está tomado de un fragmento de código del [foro de creación de aplicaciones de la Tienda Windows](http://social.msdn.microsoft.com/Forums/winappswithnativecode/thread/211ef583-db11-4e55-926b-6d9ab53dbdb4). El autor de este fragmento de código proporciona los avisos de declinación de responsabilidades y las estipulaciones siguientes:  
  
1.  C\+\+ no proporciona API específicas para aplicar reflexión en tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], pero los archivos de metadatos de Windows \(.winmd\) para un tipo son totalmente conformes a los archivos de metadatos CLR. Windows proporciona las nuevas API de detección de metadatos \(RoGetMetaDataFile\) para obtener el archivo .winmd para un tipo determinado. Sin embargo, estas API son de uso limitado para los programadores de C\+\+ porque no puedes crear instancias de una clase.  
  
2.  Una vez compilado el código, también necesitarás pasar Runtimeobject.lib y Rometadata.lib al vinculador.  
  
3.  Este fragmento de código se muestra tal cual. Aunque se espera que funcione correctamente, es posible que contenga errores.  
  
```  
  
#include <hstring.h> #include <cor.h> #include <rometadata.h> #include <rometadataresolution.h> #include <collection.h> namespace ABI_Isolation_Workaround { #include <inspectable.h> #include <WeakReference.h> } using namespace ABI_Isolation_Workaround; #include <wrl/client.h> using namespace Microsoft::WRL; using namespace Windows::Foundation::Collections; IVector<String^>^ GetTypeMethods(Object^); MainPage::MainPage() { InitializeComponent(); Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/"); auto methods = GetTypeMethods(uri); std::wstring strMethods; std::for_each(begin(methods), end(methods), [&strMethods](../standard-library/string.md methodName) { strMethods += methodName->Data(); strMethods += L"\n"; }); wprintf_s(L"%s\n", strMethods.c_str()); } IVector<String^>^ GetTypeMethods(Object^ instance) { HRESULT hr; HSTRING hStringClassName; hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ className = reinterpret_cast<String^>(hStringClassName); ComPtr<IMetaDataDispenserEx> metadataDispenser;ComPtr<IMetaDataImport2> metadataImport;hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf()); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD HSTRING hStringFileName; mdTypeDef typeDefToken; hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ fileName = reinterpret_cast<String^>(hStringFileName); HCORENUM hCorEnum = 0; mdMethodDef methodDefs[2048]; ULONG countMethodDefs = sizeof(methodDefs); hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD wchar_t methodName[1024]; ULONG countMethodName; std::wstring strMethods; Vector<String^>^ retVal = ref new Vector<String^>(); for(int i = 0; i < countMethodDefs; ++i) { countMethodName = sizeof(methodName); hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr); if (SUCCEEDED(hr)) { methodName[ countMethodName ] = 0; retVal->Append(ref new String(methodName)); } } return retVal; }  
  
```  
  
## Vea también  
 [Interoperar con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)